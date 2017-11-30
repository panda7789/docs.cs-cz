---
title: "Ověření schématu pomocí objektem XPathNavigator nastaveným na"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91ad5c2e6f8af7f2c3709b9dff65bd728de08e5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="4d5b9-102">Ověření schématu pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="4d5b9-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="4d5b9-103">Pomocí <xref:System.Xml.XmlDocument> třídu, můžete ověřit obsah XML, který je součástí <xref:System.Xml.XmlDocument> objektu dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="4d5b9-104">První způsob je ověřit obsah XML pomocí ověřování <xref:System.Xml.XmlReader> objekt a druhým způsobem je použití <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="4d5b9-105">Můžete také provést jen pro čtení ověření obsahu pomocí XML <xref:System.Xml.XPath.XPathDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="4d5b9-106">Ověřování dat XML</span><span class="sxs-lookup"><span data-stu-id="4d5b9-106">Validating XML Data</span></span>  
 <span data-ttu-id="4d5b9-107"><xref:System.Xml.XmlDocument> Třída neověřuje dokument XML pomocí DTD nebo XML schéma ověřování schématu definition language (XSD) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="4d5b9-108">Pouze ověřuje, zda je v dokumentu XML správně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="4d5b9-109">První způsob, jak ověřit dokument XML je k ověření dokumentu, jako je načten do <xref:System.Xml.XmlDocument> pomocí ověřování <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="4d5b9-110">Druhý způsob je ověřit dříve bez typu dokumentu XML pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="4d5b9-111">V obou případech může být obnoveny změny ověřené dokument XML, pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="4d5b9-112">Ověřování dokumentu po načtení</span><span class="sxs-lookup"><span data-stu-id="4d5b9-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="4d5b9-113">Ověření <xref:System.Xml.XmlReader> předáním je vytvořen objekt <xref:System.Xml.XmlReaderSettings> do objektu <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídu, která přebírá <xref:System.Xml.XmlReaderSettings> objektu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="4d5b9-114"><xref:System.Xml.XmlReaderSettings> Objekt předaný parametr má <xref:System.Xml.XmlReaderSettings.ValidationType%2A> vlastnost nastavena na hodnotu `Schema` a schéma XML pro dokument XML, které jsou součástí <xref:System.Xml.XmlDocument> objekt přidaný do jeho <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="4d5b9-115">Ověřování <xref:System.Xml.XmlReader> objekt se pak používá k vytvoření <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="4d5b9-116">V následujícím příkladu ověří `contosoBooks.xml` souborů, jako je načten do <xref:System.Xml.XmlDocument> objekt vytvořením <xref:System.Xml.XmlDocument> pomocí ověřování <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="4d5b9-117">Vzhledem k tomu, že v dokumentu XML není platná podle jeho schématu, jsou generovány žádné chyby ověřování schématu nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="4d5b9-118">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="4d5b9-119">Tento příklad také trvá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="4d5b9-120">V předchozím příkladu <xref:System.Xml.Schema.XmlSchemaValidationException> bude vyvolána při <xref:System.Xml.XmlDocument.Load%2A> je volána, pokud žádný typ elementu nebo atributu neodpovídá odpovídající typ zadaný v ověřování schématu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="4d5b9-121">Pokud <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> je nastavený na ověřování <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> bude zavolána vždy, když se zjistil neplatný typ.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="4d5b9-122"><xref:System.Xml.Schema.XmlSchemaException> Bude vyvolána, pokud atribut nebo element s <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> nastavena na `invalid` přistupuje <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="4d5b9-123"><xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Vlastnost lze použít k určení, zda jednotlivé atribut nebo element je platný při přístupu k atributy nebo elementů pomocí <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d5b9-124">Když je dokument XML načten do <xref:System.Xml.XmlDocument> objekt s přidružené schéma, která definuje výchozí hodnoty <xref:System.Xml.XmlDocument> objekt zpracovává tato výchozí nastavení, jako kdyby byly zobrazeny v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="4d5b9-125">To znamená, že <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> vlastnost vždy vrátí hodnotu `false` pro element, který byl převezme z schématu, i když v dokumentu XML byla zapsána jako prázdný element.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="4d5b9-126">Ověřování dokumentu s použitím metoda ověření</span><span class="sxs-lookup"><span data-stu-id="4d5b9-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="4d5b9-127"><xref:System.Xml.XmlDocument.Validate%2A> Metodu <xref:System.Xml.XmlDocument> třída ověří obsažené v dokumentu XML <xref:System.Xml.XmlDocument> pomocí schémat zadaný v objektu <xref:System.Xml.XmlDocument> objektu <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost a provede informační sadu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="4d5b9-128">Výsledkem je dříve bez typu dokumentu XML v <xref:System.Xml.XmlDocument> objektu nahradí typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="4d5b9-129"><xref:System.Xml.XmlDocument> Objekt sestavy chyby ověřování schématu a upozornění pomocí <xref:System.Xml.Schema.ValidationEventHandler> delegáta předány jako parametr, který se <xref:System.Xml.XmlDocument.Validate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="4d5b9-130">Následující příklad ověří `contosoBooks.xml` obsažené v souboru <xref:System.Xml.XmlDocument> objektu proti `contosoBooks.xsd` schématu obsažené v <xref:System.Xml.XmlDocument> objektu <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidateExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Dim document As XmlDocument = New XmlDocument()  
        document.Load("contosoBooks.xml")  
        Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
        Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
        document.Validate(validation)  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidateExample  
{  
    static void Main(string[] args)  
    {  
        XmlDocument document = new XmlDocument();  
        document.Load("contosoBooks.xml");  
        XPathNavigator navigator = document.CreateNavigator();  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
        ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
        document.Validate(validation);  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="4d5b9-131">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="4d5b9-132">Tento příklad také trvá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="4d5b9-133">Ověření úprav</span><span class="sxs-lookup"><span data-stu-id="4d5b9-133">Validating Modifications</span></span>  
 <span data-ttu-id="4d5b9-134">Po úprav dokumentu XML, můžete ověřit změny pro schéma pro dokument XML pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="4d5b9-135">V následujícím příkladu ověří `contosoBooks.xml` souborů, jako je načten do <xref:System.Xml.XmlDocument> objekt vytvořením <xref:System.Xml.XmlDocument> pomocí ověřování <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="4d5b9-136">V dokumentu XML je úspěšně ověřit, protože je načten bez generování všechny chyby ověřování schématu nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="4d5b9-137">V příkladu potom vytvoří dvě změny v dokumentu XML, které jsou neplatné podle `contosoBooks.xsd` schématu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="4d5b9-138">První úpravy vloží neplatným podřízeným elementem výsledkem je chyba ověření schématu a druhý úpravy nastaví hodnota typu uzlu na hodnotu, která je neplatná závislosti na typu uzlu, což vede k výjimce.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
            Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
            navigator.MoveToChild("book", "http://www.contoso.com/books")  
            navigator.MoveToChild("author", "http://www.contoso.com/books")  
  
            navigator.AppendChild("<title>Book Title</title>")  
  
            document.Validate(validation)  
  
            navigator.MoveToParent()  
            navigator.MoveToChild("price", "http://www.contoso.com/books")  
            navigator.SetTypedValue(DateTime.Now)  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
  
            ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
            navigator.MoveToChild("book", "http://www.contoso.com/books");  
            navigator.MoveToChild("author", "http://www.contoso.com/books");  
  
            navigator.AppendChild("<title>Book Title</title>");  
  
            document.Validate(validation);  
  
            navigator.MoveToParent();  
            navigator.MoveToChild("price", "http://www.contoso.com/books");  
            navigator.SetTypedValue(DateTime.Now);  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="4d5b9-139">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="4d5b9-140">Tento příklad také trvá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="4d5b9-141">V předchozím příkladu dvě změny provedené v dokumentu XML, které jsou součástí <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="4d5b9-142">Jako dokument XML byl načten, všechny chyby ověřování schématu došlo by byly zpracovávaných obslužná rutina události ověření a zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="4d5b9-143">V tomto příkladu byly zavedeny chyby ověření po dokumentu XML bylo načteno a nebyly nalezeny pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="4d5b9-144">Změny provedené pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třída výsledkem <xref:System.InvalidCastException> kvůli neplatnosti podle schématu typ uzlu novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="4d5b9-145">Další informace o změnách pomocí hodnot <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodu, najdete v části [upravit Data XML pomocí objektem XPathNavigator nastaveným](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="4d5b9-146">Ověření jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4d5b9-146">Read-Only Validation</span></span>  
 <span data-ttu-id="4d5b9-147"><xref:System.Xml.XPath.XPathDocument> Třída je jen pro čtení, v paměti reprezentace dokument XML.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="4d5b9-148">Obě <xref:System.Xml.XPath.XPathDocument> – třída a <xref:System.Xml.XmlDocument> vytvořit třídu <xref:System.Xml.XPath.XPathNavigator> objektů přejděte a úpravám dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="4d5b9-149">Protože <xref:System.Xml.XPath.XPathDocument> třídy je třída jen pro čtení, <xref:System.Xml.XPath.XPathNavigator> je vrácen objekt z <xref:System.Xml.XPath.XPathDocument> objekty obsažené v dokumentu XML nelze upravit, <xref:System.Xml.XPath.XPathDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="4d5b9-150">V případě ověření, můžete vytvořit <xref:System.Xml.XPath.XPathDocument> objektu stejně jako vytvoříte <xref:System.Xml.XmlDocument> pomocí ověřování <xref:System.Xml.XmlReader> objektu, jak je popsáno výše v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="4d5b9-151"><xref:System.Xml.XPath.XPathDocument> Objekt ověří dokumentu XML, jako je načtena, ale protože data XML v nelze upravit <xref:System.Xml.XPath.XPathDocument> objektu nelze znovu ověřit v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="4d5b9-152">Další informace o jen pro čtení a upravovat <xref:System.Xml.XPath.XPathNavigator> objekty, najdete [čtení dat XML pomocí XPathDocument třídou XMLDocument nastavenou na](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="4d5b9-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d5b9-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d5b9-153">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="4d5b9-154">Zpracování kódu XML dat pomocí jazyka XPath datový Model</span><span class="sxs-lookup"><span data-stu-id="4d5b9-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="4d5b9-155">Načítání dat XML pomocí XPathDocument a třídou XMLDocument nastavenou na</span><span class="sxs-lookup"><span data-stu-id="4d5b9-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="4d5b9-156">Výběr, Evaluating a porovnávání dat XML pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="4d5b9-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="4d5b9-157">Přístup k datům XML pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="4d5b9-157">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="4d5b9-158">Úpravy pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="4d5b9-158">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
