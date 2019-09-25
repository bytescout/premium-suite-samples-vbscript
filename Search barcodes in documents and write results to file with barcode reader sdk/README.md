## How to search barcodes in documents and write results to file with barcode reader sdk in VBScript and ByteScout Premium Suite

### How to write a robust code in VBScript to search barcodes in documents and write results to file with barcode reader sdk with this step-by-step tutorial

Every ByteScout tool includes simple example VBScript source codes that you can get here or in the folder with installed ByteScout product. What is ByteScout Premium Suite? It is the set that includes 12 SDK products from ByteScout including tools and components for PDF, barcodes, spreadsheets, screen video recording. It can help you to search barcodes in documents and write results to file with barcode reader sdk in your VBScript application.

The following code snippet for ByteScout Premium Suite works best when you need to quickly search barcodes in documents and write results to file with barcode reader sdk in your VBScript application. Just copy and paste the code into your VBScript application’s code and follow the instructions. Enjoy writing a code with ready-to-use sample VBScript codes.

ByteScout provides the free trial version of ByteScout Premium Suite along with the documentation and source code samples.

## REQUEST FREE TECH SUPPORT

[Click here to get in touch](https://bytescout.zendesk.com/hc/en-us/requests/new?subject=ByteScout%20Premium%20Suite%20Question)

or just send email to [support@bytescout.com](mailto:support@bytescout.com?subject=ByteScout%20Premium%20Suite%20Question) 

## ON-PREMISE OFFLINE SDK 

[Get Your 60 Day Free Trial](https://bytescout.com/download/web-installer?utm_source=github-readme)
[Explore SDK Docs](https://bytescout.com/documentation/index.html?utm_source=github-readme)
[Sign Up For Online Training](https://academy.bytescout.com/)


## ON-DEMAND REST WEB API

[Get your API key](https://pdf.co/documentation/api?utm_source=github-readme)
[Explore Web API Documentation](https://pdf.co/documentation/api?utm_source=github-readme)
[Explore Web API Samples](https://github.com/bytescout/ByteScout-SDK-SourceCode/tree/master/PDF.co%20Web%20API)

## VIDEO REVIEW

[https://www.youtube.com/watch?v=NEwNs2b9YN8](https://www.youtube.com/watch?v=NEwNs2b9YN8)




<!-- code block begin -->

##### ****TestBarcodeReadingFromPDF.vbs:**
    
```
' Create BarCodeReader object
Set bc = CreateObject("Bytescout.BarCodeReader.Reader")

' Limit barcode search to PDF417 barcodes only
bc.BarcodeTypesToFind.PDF417 = True

' Create File System object
Set FSO = CreateObject("Scripting.FileSystemObject")

' Get folder object (current folder)
Set objFolder = FSO.GetFolder(".")

' Get file list
Set files = objFolder.Files

' Create output file
Set TS = FSO.CreateTextFile("output.txt")

' Run barcode search for PDF and TIFF files
For Each file in files

	ext = UCase(FSO.GetExtensionName(file))	
	If ext = "PDF" Or ext = "TIF" Then
		bc.ReadFromFile file.Name
		For i = 0 To bc.FoundCount - 1
			' Write found barcode information to output file
			TS.Write("File: """ & file.Name & """ Page " & CStr(bc.GetFoundBarcodePage(i)) & ": Barcode: " & bc.GetFoundBarcodeValue(i)) & vbCRLF
		Next
    End If 
    
Next

TS.Close

Set bc = Nothing
Set TS = Nothing
Set FSO = Nothing

MsgBox "Done! See output.txt with found results"


```

<!-- code block end -->