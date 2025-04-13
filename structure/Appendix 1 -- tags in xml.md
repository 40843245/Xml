# Appendix 1 -- tags in xml
## XML Processing Instruction
An SGML processing instruction is enclosed within `<?` and `>`.

An XML processing instruction is enclosed within `<?` and `?>`.

## xml declaration 
To declares it is an xml file, place `<?xml ?>` at beginning of xml file.

Additionally, with `<?xml ?>` at beginning of xml file, you can know 

+ metadata of xml file, 
  - version info
  - encoding declaration
  - standalone or not

> [!IMPORTANT]
> Observe the format, we can unstrictly say that xml declaration is a special case of XML Processing Instruction
>
> although technically, strictly said it is not.


For more details, see the XML docs -- [Extensible Markup Language (XML) 1.0 (Fifth Edition)](https://www.w3.org/TR/REC-xml/#NT-S)

or kjhughes's answer in [What is on the first line of an XML document?](https://stackoverflow.com/questions/35835870/what-is-on-the-first-line-of-an-xml-document)

<img width="697" alt="image" src="https://github.com/user-attachments/assets/435891f8-389c-4b6c-988d-3305a8298d4f" />

<img width="731" alt="image" src="https://github.com/user-attachments/assets/da3ae305-cb0e-4178-95ec-e5a3177b37f8" />

### property in xml declaration 
| namespace in xml tag | meaning | description | notes | notice |
| :---------- | :----------- | :----- | :--- | :-- |
| `version` | version info | determines which version will XML preprocessor will use. | It is required | |
| `encoding` | encoding | determines which encoding will XML preprocessor will use. | It is optional.</br>If it is not specified, it defaults to `"UTF-8"` (if it can not be determined externally), or encoding determined externally. | |
| `standalone` | standalone | determines the xml file is standalone.  | It is optional.</br>If it is not specified, it defaults to `"no"`. | |

### examples
#### example 1

`test1.xml` file.

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
```

In the above example, we can know that

+ Will preprocess `test1.xml` file with XML preprocessor version 1.0.
+ XML preprocessor version 1.0 will encode the text in `test1.xml` file with encoding `UTF-8`.
+ `test1.xml` is standalone.

#### tag and its attribute in xml
#### tag in xml
| xml tag | meaning | description | notes | notice |
| :---------- | :----------- | :----- | :--- | :-- |
| `<Types>` | | | acts like a container that defines the content types. | | |
| `<Default>` | | | specifies the default setting of this file. | | |
| `<Override>` | | | overrides the default setting.

#### attribute in xml
##### attribute in `<Default>`
| attribute tag | meaning | description | notes | notice |
| :---------- | :----------- | :----- | :--- | :-- |
| `Extension` | | | specifies the extension will be used. | | |
| `ContentType`| | content type | specifies the content type. | | |

##### attribute in `<Override>`
| attribute tag | meaning | description | notes | notice |
| :---------- | :----------- | :----- | :--- | :-- |
| `PartName` | | | specifies the package part uri. | | |
| `ContentType`| | content type | specifies the content type. | | |

### examples
#### example 1

`test1.xml` file.

```
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
  <Default Extension="xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.document.main+xml"/>
  <Default Extension="rels" ContentType="application/vnd.openxmlformats-package.relationships+xml"/>
  <Override PartName="/word/styles.xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.styles+xml"/>
  <Override PartName="/word/numbering.xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.numbering+xml"/>
  <Override PartName="/word/settings.xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.settings+xml"/>
  <Override PartName="/word/fontTable.xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.fontTable+xml"/>
  <Override PartName="/word/theme/theme1.xml" ContentType="application/vnd.openxmlformats-officedocument.theme+xml"/>
  <Override PartName="/word/webSettings.xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.webSettings+xml"/>
</Types>
```

In above example, we can know that

+ In `<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">`, the xmlns's content type targst to `http://schemas.openxmlformats.org/package/2006/content-types`.
+ In  `<Default Extension="xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.document.main+xml"/>`, it configures xml extension, whose content type is `application/vnd.openxmlformats-officedocument.wordprocessingml.document.main+xml`.
+ In `<Override PartName="/word/settings.xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.settings+xml"/>`, it overrides the deault setting, content type of `~/word/settings.xml` file under Word file is `application/vnd.openxmlformats-officedocument.wordprocessingml.settings+xml`.

## reference
### related question
On stackoverflow, 

+ [What is on the first line of an XML document?](https://stackoverflow.com/questions/35835870/what-is-on-the-first-line-of-an-xml-document)
+ [How to remove standalone attribute declaration in xml document?](https://stackoverflow.com/questions/8438105/how-to-remove-standalone-attribute-declaration-in-xml-document#:~:text=If%20there%20are%20external%20markup%20declarations%20but%20there,document%20declaration%2C%20the%20value%20%22no%22%20is%20assumed.%22%20w3.org%2FTR%2FREC-xml%2F%23sec-rmd)
+ [How default is the default encoding (UTF-8) in the XML Declaration?](https://stackoverflow.com/questions/16361909/how-default-is-the-default-encoding-utf-8-in-the-xml-declaration)

### official docs
XML docs:

+ [Extensible Markup Language (XML) 1.0 (Fifth Edition)](https://www.w3.org/TR/REC-xml/#NT-S)

OOXML docs:

+ [OOXML](https://ooxml.info/docs)
