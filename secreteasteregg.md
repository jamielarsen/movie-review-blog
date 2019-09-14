---
layout: page
title: Cookies
background: /img/bg-see.jpg
scroll: ok
permalink: /secreteasteregg/
---

<script>
function setCookie(cookieName,cookieValue,exdays)
{
    var d = new Date();
    d.setTime(d.getTime() + (exdays*24*60*60*1000));
    var expires = "expires=" + d.toGMTString();
    document.cookie = cookieName + "=" + cookieValue + ";" + expires + ";path=/";
}

function getCookie(cookieName)
{
    var name = cookieName + "=";
    var decodedCookie = decodeURIComponent(document.cookie);
    var ca = decodedCookie.split(';');

    for(var i = 0; i < ca.length; i++)
    {
        var c = ca[i];

        while (c.charAt(0) == ' ')
        {
            c = c.substring(1);
        }

        if (c.indexOf(name) == 0)
        {
            return c.substring(name.length, c.length);
        }
    }

    return "";
}

function checkCookie()
{
    var user=getCookie("username");

    if (user !="")
    {
        alert("Yes, yes you do. Hi there " + user + "!");
    } 
    else
    {
        var confirmation1 = confirm("Apparently, you don't. Would you like to make one? You'll be famous...");
        var idontwanttobreakfree = true;

        while(idontwanttobreakfree == true)
        {
            if (confirmation1 == true)
            {
                user = prompt("Please enter your name:","");
                if (user != "" && user != null)
                {
                    setCookie("username", user, 30);
                    idontwanttobreakfree = false;
                }
                else
                {
                    alert("Your name is null? I don't think so...");
                    idontwanttobreakfree = confirm("Do you want to have another go?");

                    if (idontwanttobreakfree == true)
                    {
                        var confirmation2 = confirm("Okay, I'll let you have another go. Just as long as you promise not to be so silly this time. Press OK if you agree.");
                        if (confirmation2 == false)
                        {
                            alert("I'm done with you. I CAN'T DEAL WITH THIS ANYMORE!");
                            idontwanttobreakfree = confirmation2;
                        }
                    }
                    else
                    {
                        alert("Well then, I guess you'll never be immortalised in the form of cookie. It's your loss...");
                        idontwanttobreakfree = false
                    }
                }
            }
        }
    }
}
</script>

<hr>

<center>
    <form onsubmit="checkCookie()">
        <button type="submit">Do you have a cookie named after you?</button>
    </form>
</center>