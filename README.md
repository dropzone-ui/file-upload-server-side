<p align="center">
<img align="center" with="128px" height="128px" src="https://user-images.githubusercontent.com/43678736/132112022-0ca409ae-cca2-43c8-be89-110376260a3f.png" alt="dropone-ui-logo">

<h1 align="center">  Dropzone-UI (file-upload-server-side)</h1>
Server side implementations for uploading files.

</p>

# Express
Server side implementation for uploading files built with Express.js.


## Run server
Follow the instructions to run the server.

```sh
#clone this repository
git clone https://github.com/dropzone-ui/file-upload-server-side.git

#move to project folder
cd ./expressjs

#install dependencies
npm install

#run server on development mode
npm run dev
```

Congrats! you are done!. Your server is now running on port 2800. 
So, the url endpoint that must be given to `Dropzone` component is `http://localhost:2800/upload-my-file`.

If you deploy your server, the url prop will change to `http://<YOUR_SERVER_URL>/upload-my-file`.

# Frontend side
Now upload some files from a react app using [dropzone-ui](https://www.npmjs.com/package/@dropzone-ui/react) this way:

```jsx
import React,{ useState} from "react";
import { Dropzone, FullScreenPreview, FileItem } from "@dropzone-ui/react";

const SERVER_URL = "http://localhost:2800";

const Example = props =>{
    const [files, setFiles] = useState([]);
    const updateFiles = (incommingFiles) => {
      console.log("incomming files", incommingFiles);
      setFiles(incommingFiles);
    };
    const handleUpload=(responses)=>{
      //check the responses here
      console.log("responses", responses);
    }
    const onDelete = (id) => {
      setFiles(files.filter((x) => x.id !== id));
    };
 
    return (
      <Dropzone
        onChange={updateFiles}
        value={files}
        onUploadFinish={handleUpload}
        url={SERVER_URL + "/upload-my-file"}
      >
        {files.map((file) => (
          <FileItem
            {...file}
            key={file.id}
            onDelete={onDelete}
          />
        ))}
      </Dropzone>
    );
}
export default Example;
```

For more examples of [dropzone-ui](https://www.npmjs.com/package/@dropzone-ui/react), check [here](https://www.npmjs.com/package/@dropzone-ui/react#Usage-and-examples).

## License

This project is licensed under the terms of the
[MIT license](/LICENSE).
