# Lab 2 #
### Grace Ortiz ###

```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {

    private String searchList = "";
    private int count = 1;

    public String handleRequest(URI url) {

        String query = url.getQuery();

        if (url.getPath().equals("/")) {
            return "Add a message!";
        }
        else if (url.getPath().contains("/add-message")) { 
            if (query.equals(null) || !query.startsWith("s=")){
                return "Add a message after s= ";
            }
            else {
                String message = query.substring(2);
                searchList += String.format("%d. %s\n", count, message);
                count++;
                return searchList;
            }
        }

        else {
            if (url.getPath().equals("/clear")) {
                searchList = "";
                count = 1;
                return searchList;
            }
            return "404 Not Found!";
        }
    } 
}


class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
