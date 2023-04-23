# Lab Report 1 - Week 3 (Servers & Bugs) 

## Part 1 : String Server

**Code**

```
import java.io.IOException;
import java.net.URI;

class StringHandler implements URLHandler
{
    private String string = "";

    @Override
    public String handleRequest(URI url)
    {
        String[] param = url.getQuery() != null ? url.getQuery().split("=") : new String[0];
        String[] rawPath = url.getPath().split("/");
        int countPath = 0;
        for (String p : rawPath)
        {
            if (!p.isEmpty())
                countPath++;
        }

        String[] newpath = new String[countPath];
        countPath = 0;
        for (String p : rawPath)
        {
            if (!p.isEmpty())
            {
                newpath[countPath] = p;
                countPath++;
            }
        }

        if (newpath.length == 0)
            return "nothing here: no params";

        if (newpath[0].equals("add-message"))
        {
            if (param.length == 0)
                return "couldn't parse params: no params";

            if (param.length > 2)
                return "couldn't parse params: too many params";
            
            if (param[0].equals("s"))
            {
                string += param[1] + "\n";
                return string;
            }

            return "unrecognized param: " + param[0];
        }
        
        return "nothing here: unrecognized path";
    }
}

public class StringServer
{
    public static void main(String[] args) throws IOException
    {
        if(args.length == 0)
        {
            System.out.println("Missing port number! Try a different number!");
            return;
        }

        int temp = Integer.parseInt(args[0]);

        Server.start(temp, new StringHandler());
    }
}
```

**Examples using `/add-message`**

![Image](Labreport2-hello.png)

The URL used is `localhost:2/add-message?s=Hello`

The method `StringHandler.handleRequest(URI url)` is being called with the argument being a URI object that represents the URL which is `localhost2:2/add-message?s=Hello`. The method anaylzes the URI and changes the `StringHandler`'s `String string` field to add the `Hello` string.

![Image](Labreport2-howareyou.png)

The URL used are `localhost:2/add-message?s=How are you`

The method `StringHandler.handleRequest(URI url)` is being called with the argument being a URI object that represents the URL which is `localhost2:add-message?s=How are you`. The method anaylzes the URI and adds it to the `StringHandler`'s `String string` field to add the `How are you` string after the `Hello` string. 




