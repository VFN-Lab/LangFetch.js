
![LangFetch Cover](https://raw.githubusercontent.com/RdivxeAI/LangFetch.js/refs/heads/main/LangFetch.png)

# **LangFetch.js**

A developer-friendly JavaScript library for sending **HTTP requests** using highly flexible **natural language prompts** in Arabic or English. Supports **GET**, **POST**, **JSON**, **FormData**, **file uploads**, dynamic parameters, automatic type conversion, and repeated requests.

### **Load via CDN**

```html
<script src="https://cdn.jsdelivr.net/gh/RdivxeAI/LangFetch.js/LangFetch.js"></script>
```

---

## **Features**

* Send HTTP requests using **natural language prompts**.
* Automatic placeholder definition for variables (`window.varName`).
* Supports **GET** and **POST** requests.
* JSON, FormData, and file uploads supported.
* Automatic type conversion (`string`, `number`, `boolean`, `object`, `array`).
* Repeat requests easily with `proRepeat`.
* Fully compatible with Arabic and English prompts.
* Handles errors gracefully and logs them to the console.

---

## **Usage Examples**

### **English**

```html
<prompt style="display:none;">
Send a POST request to https://jsonplaceholder.typicode.com/posts and store the result in variable user_response of type object params: {"user":"John"}
</prompt>

<script>
  // Flexible POST request
  pro("Send the body data to https://jsonplaceholder.typicode.com/posts and store the result in responseData of type object body: {\"key\":\"value\"}");

  // GET request
  pro("Get data from https://jsonplaceholder.typicode.com/todos/1 and store in statusVar");

  // Repeat request 5 times
  proRepeat("Send POST request to https://jsonplaceholder.typicode.com/posts params: {\"event\":\"click\"} and store output in logArray", 5);

</script>
```

### **Arabic**

```html
<script src="LangFetch.js"></script>
<prompt style="display:none;">
في المتغير result2 من النوع string جيب https://example.com/api?q=query
</prompt>


<prompt style="display:none;">
ابعت البيانات لـ https://jsonplaceholder.typicode.com/posts وخزن الناتج في result_obj من النوع object بيانات: {"name":"عمرو"}
</prompt>

<script>
  // Repeat request 3 times
  proRepeat("في المتغير statusVar من النوع string جيب https://jsonplaceholder.typicode.com/todos/1 وخزن النتيجة", 3);
</script>
```

---

## **Extended Examples: File Uploads & Types**

```html
<script>
  // Initialize variables (must be on window)
  const myFile = new File(["Hello world"], "hello.txt", {type:"text/plain"});
  window.myFile = myFile;

  // File upload
  pro('في المتغير uploadResult من النوع object ارفع myFile الى https://jsonplaceholder.typicode.com/posts')
    .then(() => console.log("Upload Status:", window.uploadStatus));

  // POST JSON
  pro('في المتغير result1 من النوع object ابعت https://jsonplaceholder.typicode.com/posts params: {"key":"system_test"}')
    .then(() => console.log("POST Result:", window.result1));

  // GET request with automatic type conversion
  pro('في المتغير count من النوع number جيب https://jsonplaceholder.typicode.com/posts/1/id')
    .then(() => console.log("Count:", window.count, "Type:", typeof window.count));

  // Repeat request
  proRepeat('هات من https://jsonplaceholder.typicode.com/posts/1/title وحط النتيجة في المتغير repeatedTitle من النوع string', 2)
    .then(results => console.log("Repeated Results:", results));
</script>
```

---

## **API Reference**

| Function                                     | Description                              |
| -------------------------------------------- | ---------------------------------------- |
| `pro(promptText)`                            | Run a single natural language prompt.    |
| `proRepeat(promptText, times)`               | Run a prompt multiple times.             |
| `LangFetch.runAllPrompts()`                  | Execute all `<prompt>` tags on the page. |
| `LangFetch.definePlaceholder(varName, type)` | Manually define a placeholder variable.  |
| `LangFetch.values`                           | Access all defined placeholder values.   |

---

## **Notes**

* Variables defined in prompts are automatically created on the `window` object.
* File uploads require the file object to be saved as a global variable before referencing.
* Core keywords (`في المتغير`, `ابعت`, `params`, `ارفع`) are sufficient; extra text is ignored.
* Automatic type conversion based on placeholder type.
* Errors are logged in console without breaking the application.

---

## Example Use Cases

* Quickly test APIs with natural language prompts.
* Collect form data dynamically and send to backend.
* Automate repetitive requests with minimal code.
* Use Arabic or English prompts directly in front-end code.

---

> Written by **OmarRizk**, VFN Media Lab LLC – designed for professional developers.
