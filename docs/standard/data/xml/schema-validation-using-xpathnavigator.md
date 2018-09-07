---
title: Ověření schématu pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d2b04006c46edb29fd4fe05e63224220ed1876af
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085273"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="e2227-102">Ověření schématu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e2227-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="e2227-103">Pomocí <xref:System.Xml.XmlDocument> třídy, můžete ověřit obsah XML, který je součástí <xref:System.Xml.XmlDocument> objektu dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="e2227-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="e2227-104">První způsob je na ověřování obsahu XML pomocí ověřování <xref:System.Xml.XmlReader> objekt a druhý způsob je použít <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="e2227-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="e2227-105">Můžete také provést jen pro čtení ověření obsahu pomocí XML <xref:System.Xml.XPath.XPathDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="e2227-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="e2227-106">Ověřování dat XML</span><span class="sxs-lookup"><span data-stu-id="e2227-106">Validating XML Data</span></span>  
 <span data-ttu-id="e2227-107"><xref:System.Xml.XmlDocument> Třídy nelze ověřit dokument XML pomocí DTD nebo XML definice jazyk (XSD) schématu schémat ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e2227-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="e2227-108">Pouze ověří, že dokument XML má správný formát.</span><span class="sxs-lookup"><span data-stu-id="e2227-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="e2227-109">První způsob ověření dokumentu XML je k ověření dokumentu, jako je načten do <xref:System.Xml.XmlDocument> ověřování pomocí <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="e2227-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="e2227-110">Druhý způsob je ověřit dříve netypové pomocí dokumentu XML <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="e2227-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="e2227-111">V obou případech se změny ověřené dokumentu XML můžete ověřit pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="e2227-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="e2227-112">Ověřování dokumentu po načtení</span><span class="sxs-lookup"><span data-stu-id="e2227-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="e2227-113">Ověřování <xref:System.Xml.XmlReader> předáním je vytvořen objekt <xref:System.Xml.XmlReaderSettings> objektu <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídu, která přebírá <xref:System.Xml.XmlReaderSettings> objektu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="e2227-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="e2227-114"><xref:System.Xml.XmlReaderSettings> Objekt předán jako parametr <xref:System.Xml.XmlReaderSettings.ValidationType%2A> vlastnost nastavena na hodnotu `Schema` a schéma XML pro dokument XML, který je součástí <xref:System.Xml.XmlDocument> objekt přidaný do jeho <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e2227-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="e2227-115">Ověřování <xref:System.Xml.XmlReader> objekt se pak použije k vytvoření <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="e2227-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="e2227-116">Následující příklad ověří `contosoBooks.xml` sdílené, jak je načten do <xref:System.Xml.XmlDocument> objektu tak, že vytvoříte <xref:System.Xml.XmlDocument> ověřování pomocí <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="e2227-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="e2227-117">Vzhledem k tomu, že je platný podle jeho schématu dokumentu XML, vygenerují se upozornění ani chyby ověřování schématu.</span><span class="sxs-lookup"><span data-stu-id="e2227-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
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
  
 <span data-ttu-id="e2227-118">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="e2227-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="e2227-119">Tento příklad využívá taky `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="e2227-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="e2227-120">V předchozím příkladu <xref:System.Xml.Schema.XmlSchemaValidationException> bude vyvolána při <xref:System.Xml.XmlDocument.Load%2A> je volána, pokud libovolný typ atributu nebo elementu se neshoduje s odpovídající typ zadaný v ověřování schématu.</span><span class="sxs-lookup"><span data-stu-id="e2227-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="e2227-121">Pokud <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> je nastaven ověřování <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> bude volána pokaždé, když se zjistil se neplatný typ.</span><span class="sxs-lookup"><span data-stu-id="e2227-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="e2227-122"><xref:System.Xml.Schema.XmlSchemaException> Bude vyvolána, pokud atribut nebo element s <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> nastavena na `invalid` přistupuje <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="e2227-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="e2227-123"><xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Vlastnost lze použít k určení, zda jednotlivé atribut nebo element je platné při přístupu k atributů nebo elementů s <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="e2227-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2227-124">Po načtení dokumentu XML do <xref:System.Xml.XmlDocument> objekt s přidružené schéma, který definuje výchozí hodnoty <xref:System.Xml.XmlDocument> objekt zpracuje, tyto výchozí hodnoty jako jsou uvedeny v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e2227-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="e2227-125">To znamená, že <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> vždy vrátí vlastnost `false` pro element, který byl i v případě, že v dokumentu XML byla zapsána jako prázdný element převezme ve schématu.</span><span class="sxs-lookup"><span data-stu-id="e2227-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="e2227-126">Ověřování dokumentu pomocí metody ověřování</span><span class="sxs-lookup"><span data-stu-id="e2227-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="e2227-127"><xref:System.Xml.XmlDocument.Validate%2A> Metodu <xref:System.Xml.XmlDocument> třídy ověří dokumentu XML, který je součástí <xref:System.Xml.XmlDocument> objektu pomocí schémat zadané v <xref:System.Xml.XmlDocument> objektu <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost a provádí informační sadu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="e2227-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="e2227-128">Výsledkem je dříve netypový kód XML dokumentu v <xref:System.Xml.XmlDocument> objektu nahradí zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="e2227-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="e2227-129"><xref:System.Xml.XmlDocument> Objekt hlásí chyby ověřování schématu a upozornění pomocí <xref:System.Xml.Schema.ValidationEventHandler> delegát předaný jako parametr <xref:System.Xml.XmlDocument.Validate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e2227-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="e2227-130">Následující příklad ověří `contosoBooks.xml` obsažené v souboru <xref:System.Xml.XmlDocument> objektu proti `contosoBooks.xsd` obsažené ve schématu <xref:System.Xml.XmlDocument> objektu <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e2227-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="e2227-131">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="e2227-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="e2227-132">Tento příklad využívá taky `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="e2227-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="e2227-133">Ověření úprav</span><span class="sxs-lookup"><span data-stu-id="e2227-133">Validating Modifications</span></span>  
 <span data-ttu-id="e2227-134">Po provedení změny do dokumentu XML, můžete ověřit změny schématu pro používání dokumentu XML <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="e2227-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="e2227-135">Následující příklad ověří `contosoBooks.xml` sdílené, jak je načten do <xref:System.Xml.XmlDocument> objektu tak, že vytvoříte <xref:System.Xml.XmlDocument> ověřování pomocí <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="e2227-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="e2227-136">Dokument XML proběhne úspěšně, protože je načtena bez generování upozornění ani chyby ověřování schématu.</span><span class="sxs-lookup"><span data-stu-id="e2227-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="e2227-137">Příklad poté vytvoří dvě změny v dokumentu XML, které jsou neplatné podle `contosoBooks.xsd` schématu.</span><span class="sxs-lookup"><span data-stu-id="e2227-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="e2227-138">První úpravy vloží neplatný podřízený element výsledkem je chyba ověření schématu a druhý změnu nastaví hodnotu typu uzlu na hodnotu, která je neplatná podle typu uzlu, což vede k výjimce.</span><span class="sxs-lookup"><span data-stu-id="e2227-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
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
  
 <span data-ttu-id="e2227-139">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="e2227-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="e2227-140">Tento příklad využívá taky `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="e2227-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="e2227-141">V předchozím příkladu se provádí dva úpravy dokumentu XML, který je součástí <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="e2227-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="e2227-142">Jako dokument XML byl načten, žádné chyby ověřování schématu došlo k by byly zpracovány metodu obslužné rutiny události ověření a zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="e2227-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="e2227-143">V tomto příkladu byly zavedeny chyby ověření po dokumentu XML byl načten a našly se pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="e2227-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="e2227-144">Změny provedené pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy vedlo <xref:System.InvalidCastException> protože nová hodnota nebyl platný podle schématu typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="e2227-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="e2227-145">Další informace o změně hodnot pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodu, najdete v článku [upravit dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="e2227-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="e2227-146">Ověřování jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e2227-146">Read-Only Validation</span></span>  
 <span data-ttu-id="e2227-147"><xref:System.Xml.XPath.XPathDocument> Třídy je jen pro čtení, v paměti reprezentace dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e2227-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="e2227-148">Oba <xref:System.Xml.XPath.XPathDocument> třídy a <xref:System.Xml.XmlDocument> vytvoření třídy <xref:System.Xml.XPath.XPathNavigator> objekty k procházení a úpravy dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="e2227-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="e2227-149">Protože <xref:System.Xml.XPath.XPathDocument> třídy je třída jen pro čtení, <xref:System.Xml.XPath.XPathNavigator> objekt uživatele vrácený <xref:System.Xml.XPath.XPathDocument> objekty nelze upravit obsažené v dokumentu XML <xref:System.Xml.XPath.XPathDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="e2227-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="e2227-150">V případě ověřování, můžete vytvořit <xref:System.Xml.XPath.XPathDocument> stejně jako můžete vytvořit objekt <xref:System.Xml.XmlDocument> ověřování pomocí <xref:System.Xml.XmlReader> objektu, jak je popsáno výše v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="e2227-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="e2227-151"><xref:System.Xml.XPath.XPathDocument> Objekt ověří dokumentu XML, jako je načtena, ale protože nelze upravit XML data <xref:System.Xml.XPath.XPathDocument> objektu nelze znovu ověřit dokument XML.</span><span class="sxs-lookup"><span data-stu-id="e2227-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="e2227-152">Další informace o jen pro čtení a upravovat <xref:System.Xml.XPath.XPathNavigator> objekty, najdete [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="e2227-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2227-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2227-153">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="e2227-154">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="e2227-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="e2227-155">Načítání dat XML pomocí XPathDocument a XmlDocument</span><span class="sxs-lookup"><span data-stu-id="e2227-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
- [<span data-ttu-id="e2227-156">Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e2227-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="e2227-157">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e2227-157">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="e2227-158">Úpravy dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e2227-158">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
