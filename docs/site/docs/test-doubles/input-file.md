---
uid: input-file
title: Uploading files to the InputFile component
---

# Uploading files to the `InputFile` component

bUnit comes with integrated support for the [`InputFile`](https://docs.microsoft.com/en-us/aspnet/core/blazor/file-uploads?view=aspnetcore-6.0&pivots=server) component and makes it easy to simulate uploading files.

To upload a file, first find the `InputFile` component in the component under test. Afterwards call the method `UploadFile`:

```csharp
using var ctx = new TestContext();

// Create an InputFileContent with string content
InputFileContent fileToUpload = InputFileContent.CreateFromText("Text content", "Filename.txt");

// Render the component under test which contains the InputFile component as a child component
IRenderedComponent<ComponentUnderTest> cut = ctx.RenderComponent<ComponentUnderTest>();

// Find the InputFile component
IRenderedComponent<InputFile> inputFile = cut.FindComponent<InputFile>();

// Upload the file to upload to the InputFile component
inputFile.UploadFile(fileToUpload);

// Assertions...
```

To upload binary content, create an `InputFileContent`  with the `InputFileContent.CreateFromBinary()` method.
See all supported properties supported by the `InputFileContent` on its [reference page](xref:Bunit.InputFileContent).