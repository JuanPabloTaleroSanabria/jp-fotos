<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Revista Digital Interactiva</title>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/turn.js/4.1.0/turn.min.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background: #f4f4f4;
        }
        #upload {
            margin: 20px;
        }
        #magazine {
            width: 800px;
            height: 600px;
            margin: auto;
            display: none;
        }
        .page {
            width: 800px;
            height: 600px;
            background: white;
            display: flex;
            align-items: center;
            justify-content: center;
            border: 1px solid #ddd;
            box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
        }
        .page img {
            max-width: 100%;
            max-height: 100%;
            object-fit: cover;
        }
    </style>
</head>
<body>

    <h1>📖 Crea tu Revista Digital 📖</h1>
    <input type="file" id="upload" multiple accept="image/*">
    <div id="magazine"></div>

    <script>
        $(document).ready(function() {
            $("#upload").on("change", function(event) {
                let files = event.target.files;
                let magazine = $("#magazine");
                magazine.empty();

                for (let i = 0; i < files.length; i++) {
                    let reader = new FileReader();
                    reader.onload = function(e) {
                        let page = $("<div class='page'></div>");
                        let img = $("<img>").attr("src", e.target.result);
                        page.append(img);
                        magazine.append(page);
                    };
                    reader.readAsDataURL(files[i]);
                }

                setTimeout(() => {
                    magazine.show();
                    magazine.turn({
                        width: 800,
                        height: 600,
                        autoCenter: true
                    });
                }, 500);
            });
        });
    </script>

</body>
</html>
