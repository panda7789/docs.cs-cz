---
title: Ověření schématu pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: bfcbf7306e896af54808c49e25f95d0631f5bcc0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710203"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="a4633-102">Ověření schématu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a4633-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="a4633-103">Pomocí třídy <xref:System.Xml.XmlDocument> lze ověřit obsah XML obsažený v objektu <xref:System.Xml.XmlDocument> dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="a4633-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="a4633-104">Prvním způsobem je ověřit obsah XML pomocí ověřování objektu <xref:System.Xml.XmlReader> a druhým způsobem je použít metodu <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4633-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="a4633-105">Pomocí třídy <xref:System.Xml.XPath.XPathDocument> můžete také provádět ověřování obsahu XML jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="a4633-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="a4633-106">Ověřování dat XML</span><span class="sxs-lookup"><span data-stu-id="a4633-106">Validating XML Data</span></span>  
 <span data-ttu-id="a4633-107">Třída <xref:System.Xml.XmlDocument> neověřuje dokument XML pomocí standardu DTD nebo schématu XSD (XML Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="a4633-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="a4633-108">Ověřuje pouze to, zda je dokument XML ve správném formátu.</span><span class="sxs-lookup"><span data-stu-id="a4633-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="a4633-109">Prvním způsobem, jak ověřit dokument XML, je ověřit dokument tak, jak je načten do objektu <xref:System.Xml.XmlDocument> pomocí ověřování objektu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a4633-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="a4633-110">Druhým způsobem je ověřit dříve Netypový dokument XML pomocí metody <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4633-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="a4633-111">V obou případech lze změny ověřeného dokumentu XML znovu ověřit pomocí metody <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4633-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="a4633-112">Ověřování dokumentu při jeho načtení</span><span class="sxs-lookup"><span data-stu-id="a4633-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="a4633-113">Ověřování objektu <xref:System.Xml.XmlReader> je vytvořeno předáním objektu <xref:System.Xml.XmlReaderSettings> do metody <xref:System.Xml.XmlReader.Create%2A> třídy <xref:System.Xml.XmlReader>, která přebírá objekt <xref:System.Xml.XmlReaderSettings> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="a4633-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="a4633-114">Objekt <xref:System.Xml.XmlReaderSettings> předaný jako parametr má vlastnost <xref:System.Xml.XmlReaderSettings.ValidationType%2A> nastavenou na `Schema` a schéma XML pro dokument XML obsažený v objektu <xref:System.Xml.XmlDocument> přidaného do jeho <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a4633-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="a4633-115">K vytvoření objektu <xref:System.Xml.XmlDocument> se pak použije ověřování objektu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a4633-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="a4633-116">Následující příklad ověřuje `contosoBooks.xml` soubor tak, jak je načten do objektu <xref:System.Xml.XmlDocument> vytvořením objektu <xref:System.Xml.XmlDocument> pomocí ověřování objektu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a4633-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="a4633-117">Vzhledem k tomu, že dokument XML je podle jeho schématu platný, nejsou generovány žádné chyby ověřování schématu ani upozornění.</span><span class="sxs-lookup"><span data-stu-id="a4633-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
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
  
 <span data-ttu-id="a4633-118">Příklad přebírá soubor `contosoBooks.xml` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="a4633-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="a4633-119">Příklad také přebírá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="a4633-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="a4633-120">V předchozím příkladu se <xref:System.Xml.Schema.XmlSchemaValidationException> vyvolá při volání <xref:System.Xml.XmlDocument.Load%2A>, pokud jakýkoli typ atributu nebo elementu neodpovídá odpovídajícímu typu zadanému v ověřovacím schématu.</span><span class="sxs-lookup"><span data-stu-id="a4633-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="a4633-121">Pokud je pro ověřování <xref:System.Xml.XmlReader>nastavena <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> bude volána vždy, když dojde k neplatnému typu.</span><span class="sxs-lookup"><span data-stu-id="a4633-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="a4633-122"><xref:System.Xml.Schema.XmlSchemaException> bude vyvolána, pokud k atributu nebo elementu s <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> nastaveným na `invalid` má <xref:System.Xml.XPath.XPathNavigator>k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a4633-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="a4633-123">Vlastnost <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> lze použít k určení, zda je nebo není jednotlivý atribut nebo element platný při přístupu k atributům nebo prvkům s <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="a4633-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4633-124">Při načtení dokumentu XML do objektu <xref:System.Xml.XmlDocument> s přidruženým schématem, které definuje výchozí hodnoty, objekt <xref:System.Xml.XmlDocument> zpracovává tyto výchozí hodnoty, jako by se zobrazily v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a4633-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="a4633-125">To znamená, že vlastnost <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> vždy vrátí `false` pro prvek, který byl nastaven jako výchozí ve schématu, i v případě, že v dokumentu XML byl zapsán jako prázdný prvek.</span><span class="sxs-lookup"><span data-stu-id="a4633-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="a4633-126">Ověření dokumentu pomocí metody Validate</span><span class="sxs-lookup"><span data-stu-id="a4633-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="a4633-127">Metoda <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument> ověřuje dokument XML obsažený v objektu <xref:System.Xml.XmlDocument> proti schématům zadaným ve vlastnosti <xref:System.Xml.XmlDocument.Schemas%2A> objektu <xref:System.Xml.XmlDocument> a provádí rozšíření informačního souboru.</span><span class="sxs-lookup"><span data-stu-id="a4633-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="a4633-128">Výsledkem je dříve Netypový dokument XML v objektu <xref:System.Xml.XmlDocument> nahrazený typovým dokumentem.</span><span class="sxs-lookup"><span data-stu-id="a4633-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="a4633-129">Objekt <xref:System.Xml.XmlDocument> hlásí chyby ověřování schématu a upozornění pomocí <xref:System.Xml.Schema.ValidationEventHandler> delegáta předaného jako parametr metodě <xref:System.Xml.XmlDocument.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="a4633-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="a4633-130">Následující příklad ověří `contosoBooks.xml` soubor obsažený v objektu <xref:System.Xml.XmlDocument> proti schématu `contosoBooks.xsd` obsaženému ve vlastnosti <xref:System.Xml.XmlDocument.Schemas%2A> objektu <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4633-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="a4633-131">Příklad přebírá soubor `contosoBooks.xml` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="a4633-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="a4633-132">Příklad také přebírá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="a4633-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="a4633-133">Ověřování změn</span><span class="sxs-lookup"><span data-stu-id="a4633-133">Validating Modifications</span></span>  
 <span data-ttu-id="a4633-134">Po provedení úprav dokumentu XML můžete ověřit změny schématu pro dokument XML pomocí metody <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4633-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="a4633-135">Následující příklad ověřuje `contosoBooks.xml` soubor tak, jak je načten do objektu <xref:System.Xml.XmlDocument> vytvořením objektu <xref:System.Xml.XmlDocument> pomocí ověřování objektu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a4633-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="a4633-136">Dokument XML se úspěšně ověřuje, protože je načtený bez generování chyb nebo upozornění ověřování schématu.</span><span class="sxs-lookup"><span data-stu-id="a4633-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="a4633-137">Příklad následně provede dvě úpravy dokumentu XML, které jsou podle schématu `contosoBooks.xsd` neplatné.</span><span class="sxs-lookup"><span data-stu-id="a4633-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="a4633-138">První změna vloží neplatný podřízený element, který má za následek chybu ověřování schématu a druhá změna nastaví hodnotu typovaného uzlu na hodnotu, která je neplatná podle typu uzlu, který je výsledkem výjimky.</span><span class="sxs-lookup"><span data-stu-id="a4633-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
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
  
 <span data-ttu-id="a4633-139">Příklad přebírá soubor `contosoBooks.xml` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="a4633-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="a4633-140">Příklad také přebírá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="a4633-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="a4633-141">V předchozím příkladu jsou provedeny dvě úpravy dokumentu XML obsaženého v objektu <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4633-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="a4633-142">Jak byl načten dokument XML, jakékoli zjištěné chyby ověřování schématu by byly zpracovány metodou obslužné rutiny události ověřování a zapsány do konzoly.</span><span class="sxs-lookup"><span data-stu-id="a4633-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="a4633-143">V tomto příkladu byly chyby ověřování představeny po načtení dokumentu XML a byly nalezeny pomocí metody <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4633-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="a4633-144">Změny provedené pomocí metody <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> třídy <xref:System.Xml.XPath.XPathNavigator> způsobily <xref:System.InvalidCastException>, protože nová hodnota byla podle typu schématu uzlu neplatná.</span><span class="sxs-lookup"><span data-stu-id="a4633-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="a4633-145">Další informace o úpravách hodnot pomocí metody <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> naleznete v tématu [Úprava dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="a4633-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="a4633-146">Ověřování jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4633-146">Read-Only Validation</span></span>  
 <span data-ttu-id="a4633-147">Třída <xref:System.Xml.XPath.XPathDocument> je reprezentace dokumentu XML, která je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="a4633-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="a4633-148">Třída <xref:System.Xml.XPath.XPathDocument> i třída <xref:System.Xml.XmlDocument> vytvářejí objekty <xref:System.Xml.XPath.XPathNavigator> pro procházení a úpravy dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="a4633-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="a4633-149">Vzhledem k tomu, že třída <xref:System.Xml.XPath.XPathDocument> je třída, která je jen pro čtení, vrácený objekt <xref:System.Xml.XPath.XPathNavigator> objektů <xref:System.Xml.XPath.XPathDocument> nemůže upravovat dokument XML obsažený v objektu <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4633-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="a4633-150">V případě ověřování můžete vytvořit objekt <xref:System.Xml.XPath.XPathDocument> stejným způsobem jako objekt <xref:System.Xml.XmlDocument> pomocí ověřování <xref:System.Xml.XmlReader> objektu, jak je popsáno výše v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="a4633-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="a4633-151">Objekt <xref:System.Xml.XPath.XPathDocument> ověří dokument XML, jak je načten, ale vzhledem k tomu, že data XML nelze upravovat v objektu <xref:System.Xml.XPath.XPathDocument>, nelze znovu ověřit dokument XML.</span><span class="sxs-lookup"><span data-stu-id="a4633-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="a4633-152">Další informace o objektech jen pro čtení a upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů najdete v tématu věnovaném [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) .</span><span class="sxs-lookup"><span data-stu-id="a4633-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4633-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4633-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="a4633-154">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="a4633-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="a4633-155">Načítání dat XML pomocí XPathDocument a XmlDocument</span><span class="sxs-lookup"><span data-stu-id="a4633-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="a4633-156">Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a4633-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="a4633-157">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a4633-157">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="a4633-158">Úpravy dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a4633-158">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
