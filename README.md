## Reflection 1

The handle_connection function begins by taking a TCP stream as input, which represents an active connection from a web browser sending an HTTP request. It then wraps this stream, which has been set as mutable, with a buffered reader. This buffering helps reduce the number of system calls required. 

Since the stream is now buffered, it allows reading the content line by line using the lines method. Each line is processed using the map function to extract its value, assuming that all lines are read successfully. The function continues reading until it encounters an empty line, which indicates the end of the HTTP header section. The collected lines are stored in a vector of strings and then displayed in a structured format using the println function.


## Reflection 2


![image info](image/Reflection2image.png)


This function follows the same approach as handle connection but with a key difference. After reading the request, it generates an HTTP response that includes a status line specifying the version, status code, and message. It also includes the content length, which indicates the size of the data being sent, followed by the actual HTML content that the browser will process.

To achieve this, the function first stores these elements as separate string variables. Using string formatting, it constructs the response and then sends it back to the stream as bytes, allowing the browser to render the content correctly.