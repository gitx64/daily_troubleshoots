in bash < and > works almost same like direction operators but used for different purposes.

< is used for input, > is used for output

so when we use << EOF this means if EOF is sent into input append, then the input session will be closed after that. until that it will continuously check the input if its EOF or not. and this whole thing we can redirect to >> or > operator to a new file to store the values it returns.
