# MERN Powered Web Chat App
A full-stack MERN chat application that enables authenticated user to add, view, comment & like posts. they can as well add/remove friends.

## Client(Frontend) Section
- [x] Create a new react app using npx.
- First ensure you have npx globally installed in your system.
```bash
npm i -g npx
```
- Use npx to create a new react app in the root folder like so:
```shell
npx create-react-app client
```
- Change Directory(cd) into the newly created react app then install the necessary packages.

```shell
npm i react-redux @reduxjs/toolkit redux-persist react-dropzone dotenv formik yup react-router-dom@6 @mui/material @emotion/react @emotion/styled @mui/icons-material
```

## Server 
- This entails the server configuration & set up.
#### Set up Express Routes

```javascript
import express mongoose, cors, multer, helmet,  morgan, path, from "wherever";

/* CONFIGURATIONS & MIDDLEWARE SETUP*/

const __dirname = path.dirname(fileURLToPath(import.meta.url));
const app = express();
app.use(express.json());

/* SET UP FILE STORAGE */
const storage = multer.diskStorage({
  destination: function (req, file, cb) {
    cb(null, "public/assets");
  },
  filename: function (req, file, cb) {
    cb(null, file.originalname);
  },
});
const upload = multer({ storage });

/* ROUTE WITH FILES */
app.post('/auth/register', upload.single("picture"), register);

/* SETUP MONGOSOE*/
const PORT = process.env.PORT || 6001;
mongoose
  .connect(process.env.MONGO_URL, {
    useNewUrlParser: true,
    useUnifiedTopology: true,
  })
  .then(() => {
    app.listen(PORT, () => console.log(`Server Port: ${PORT}`));
  })
  .catch((error) => console.log(`${error} did not connect`));
```

### Resources
1. [Salt & Hash passwords with bcrypt](https://heynode.com/blog/2020-04/salt-and-hash-passwords-bcrypt/)
2. [React Single File Upload Tutorial with Multer, Node, Express](https://www.positronx.io/react-file-upload-tutorial-with-node-express-and-multer/)
3. 