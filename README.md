# python_chatbot_and_api_deployment
1. Download this solution and place somewhere in your drive.
2. Install required libraries.
3. Open cmd on your project directory.
4. Type python app.py after successfully run the command you will see the info below.
5. ![image](https://user-images.githubusercontent.com/26793604/120877685-8da46800-c5d5-11eb-85a4-a88d407a1573.png)
6. Copy the localhost link and paste on browser and click enter.
7. Now using the HTML,Visual Studio, php and java copy the below html and css and javascript code.
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
<style>
   
    * {
        box-sizing: border-box;
    }

    /* Button used to open the chat form - fixed at the bottom of the page */
    .open-button {
        background-color: #555;
        color: white;
        padding: 16px 20px;
        border: none;
        cursor: pointer;
        opacity: 0.8;
        position: fixed;
        bottom: 23px;
        right: 28px;
        width: 280px;
    }

    /* The popup chat - hidden by default */
    .chat-popup {
        display: none;
        position: fixed;
        bottom: 0;
        right: 15px;
        border: 3px solid #f1f1f1;
        z-index: 9;
        width: 330px;
        background: #fff;
    }

    /* Add styles to the form container */
    .form-container {
        /*max-width: 300px;
        padding: 10px;
        background-color: white;
        height: 315px;*/
    }

        /* Full-width textarea */
        .form-container textarea {
            width: 100%;
            padding: 15px;
            margin: 5px 0 22px 0;
            border: none;
            background: #f1f1f1;
            resize: none;
            min-height: 200px;
        }

            /* When the textarea gets focus, do something */
            .form-container textarea:focus {
                background-color: #ddd;
                outline: none;
            }

        /* Set a style for the submit/send button */
        .form-container .btn {
            background-color: #04AA6D;
            color: white;
            padding: 16px 20px;
            border: none;
            cursor: pointer;
            width: 100%;
            margin-bottom: 10px;
            opacity: 0.8;
        }

        /* Add a red background color to the cancel button */
        .form-container .cancel {
            background-color: red;
        }

        /* Add some hover effects to buttons */
        .form-container .btn:hover, .open-button:hover {
            opacity: 1;
        }


    .btn-warning {
        color: #fff;
        background-color: #f08f00;
        border-color: #c27400;
    }

    .btn.btn-warning:active, .btn.btn-warning:focus, .btn.btn-warning:hover {
        box-shadow: 0 14px 26px -12px rgba(255,152,0,.42),0 4px 23px 0 rgba(0,0,0,.12),0 8px 10px -5px rgba(255,152,0,.2);
    }

    button, input, optgroup, select, textarea {
        margin: 0;
        font-family: inherit;
        font-size: inherit;
        line-height: inherit;
        overflow: visible;
    }

    #chatbox {
        /* background-color: cyan;
        margin-left: auto;
        margin-right: auto;*/
        width: 100%;
        min-height: 60px;
        margin-top: 40px;
    }

    #userInput {
        margin-left: auto;
        margin-right: auto;
        width: 40%;
        margin-top: 60px;
    }

    #textInput {
        width: 87%;
        border: none;
        border-bottom: 3px solid #009688;
        font-family: monospace;
        font-size: 17px;
    }

    #buttonInput {
        padding: 3px;
        font-family: monospace;
        font-size: 17px;
    }

    .userText {
        color: white;
        font-family: monospace;
        font-size: 17px;
        text-align: right !important;
        line-height: 30px;
        margin: 5px;
    }

        .userText span {
            background-color: #009688;
            padding: 10px;
            border-radius: 2px;
        }

    .botText {
        color: white;
        font-family: monospace;
        font-size: 17px;
        text-align: left;
        line-height: 30px;
        margin: 5px;
    }

        .botText span {
            background-color: #ef5350;
            padding: 10px;
            border-radius: 2px;
        }

    #tidbit {
        position: absolute;
        bottom: 0;
        right: 0;
        width: 300px;
    }
</style>
<button class="open-button" onclick="openForm()">Chat</button>

<div class="chat-popup" id="myForm">
    <div class="row">
        <div class="col-md-10 mr-auto ml-auto">
            <h1>AI ChatBot</h1>
            <form id="form-chat" class="form-container">
                <div id="chatbox">
                    <div class="col-md-8 ml-auto mr-auto">
                        <p class="botText" style="width:200px;"><span>Hi! I'm Your bot.</span></p><br />
                    </div>
                </div>
                <div id="userInput" class="row" style="width:120%">
                    <div class="col-md-10">
                        <input id="text" type="text" name="msg" placeholder="Message" class="form-control">
                        <button type="submit" id="send" class="btn btn-warning">Send</button>
                        <button type="button" class="btn cancel" onclick="closeForm()">Close</button>
                    </div>
                </div>
            </form>
            </div>
        </div>
        </div>

        <script>
            $(document).ready(function () {
                $("#form-chat").on("submit", function (event) {
                    
                    var rawText = $("#text").val();
                    var userHtml = '<p class="userText"><span>' + rawText + "</span></p><br>";
                    $("#text").val("");
                    $("#chatbox").append(userHtml);
                    document.getElementById("userInput").scrollIntoView({
                        block: "start",
                        behavior: "smooth",
                    });
                    $.ajax({
                        data: {
                            msg: rawText,
                        },
                        type: "POST",
                        url: "http://localhost:5000/get",
                    }).done(function (data) {
                        var botHtml = '<p class="botText"><span>' + data + "</span></p>";
                        $("#chatbox").append($.parseHTML(botHtml));
                        document.getElementById("userInput").scrollIntoView({
                            block: "start",
                            behavior: "smooth",
                        });
                    });
                    event.preventDefault();
                });
            });
            function openForm() {
                document.getElementById("myForm").style.display = "block";
            }

            function closeForm() {
                document.getElementById("myForm").style.display = "none";
            }
        </script>
        
8. Run your code in the specific IDE.
9. It will be look like below...
10. ![image](https://user-images.githubusercontent.com/26793604/120878068-a9107280-c5d7-11eb-93d3-c60aba231de4.png)
11. Job done!!!
12. Happy Coding...! :)

