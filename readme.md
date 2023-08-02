1. Create a new folder for the Project

 `mkdir go-gqlgen`




2. Mod init your project, give it whatever name you like

   `go mod init go-gqlgen`




3. Get gql gen for your project

 `go get github.com/99designs/gqlgen`




4. Add gqlgen to tools.go

 `printf '// +build tools\npackage tools\nimport _ "github.com/99designs/gqlgen"' | gofmt > tools.go`




5. Get all the dependencies

 `go mod tidy`




6. Initialize your project

`go run github.com/99designs/gqlgen init`




7. After you've written the graphql schema, run this - 

 `go run github.com/99designs/gqlgen generate`




8. To run the project - 

  `go run ./server.go`




9. to autoRestart the server - 

  `run command - fresh` if the binaries were installed



query GetBookByID($id: ID!) {
  job(id: $id) {
    _id
    title
    author
    description
    # Add other fields you want to retrieve
  }
}

{
  "id": "64ba8051b2030d5889a69e06"
}




query GetBooks() {
  jobs() {
    _id
    title
    author
    description
    addedOn
    # Add other fields you want to retrieve
  }
}



mutation CreateBookListing($input : CreateBookListingInput!){
  createBookListing(input : $input){
    _id  
    author
    description
    title
  }
}

{
  "input" : {
  "description" : "abc",
	"title" : "Harry potter",
  "author" : "paramjeet khatri"
	}
}




mutation UpdateBooks($id: ID!,$input : UpdateBookListingInput!){
  UpdateBooks(id: $id,input : $input){
    title
    description
    author
  }
}

{
  "id": "64c9f5884c527ec82e6358b4",
  "input" : {
  "description" : "abc",
  "title" : "Harry potter khatri",
  "author" : "paramjeet khatri"
	}
}




query book($author: String!) {
  book(author: $author) {
    title
    author
    description
    addedOn
    # Add other fields if needed
  }
}

{
  "author": "paramjeet"
}



mutation DeleteBook($id: ID!) {
  deleteBookById(id: $id) {
    DeletedBookID
  }
}

{
  "id": "64c9f33a4c527ec82e6358b2"
}





