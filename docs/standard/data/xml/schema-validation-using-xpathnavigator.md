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
ms.openlocfilehash: 335e6578767c130760f322aa2b015ea7b0f317f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026988"
---
# <a name="schema-validation-using-xpathnavigator"></a>Ověření schématu pomocí XPathNavigator
Pomocí <xref:System.Xml.XmlDocument> třídy, můžete ověřit obsah XML, který je součástí <xref:System.Xml.XmlDocument> objektu dvěma způsoby. První způsob je na ověřování obsahu XML pomocí ověřování <xref:System.Xml.XmlReader> objekt a druhý způsob je použít <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy. Můžete také provést jen pro čtení ověření obsahu pomocí XML <xref:System.Xml.XPath.XPathDocument> třídy.  
  
## <a name="validating-xml-data"></a>Ověřování dat XML  
 <xref:System.Xml.XmlDocument> Třídy nelze ověřit dokument XML pomocí DTD nebo XML definice jazyk (XSD) schématu schémat ve výchozím nastavení. Pouze ověří, že dokument XML má správný formát.  
  
 První způsob ověření dokumentu XML je k ověření dokumentu, jako je načten do <xref:System.Xml.XmlDocument> ověřování pomocí <xref:System.Xml.XmlReader> objektu. Druhý způsob je ověřit dříve netypové pomocí dokumentu XML <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy. V obou případech se změny ověřené dokumentu XML můžete ověřit pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Ověřování dokumentu po načtení  
 Ověřování <xref:System.Xml.XmlReader> předáním je vytvořen objekt <xref:System.Xml.XmlReaderSettings> objektu <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídu, která přebírá <xref:System.Xml.XmlReaderSettings> objektu jako parametr. <xref:System.Xml.XmlReaderSettings> Objekt předán jako parametr <xref:System.Xml.XmlReaderSettings.ValidationType%2A> vlastnost nastavena na hodnotu `Schema` a schéma XML pro dokument XML, který je součástí <xref:System.Xml.XmlDocument> objekt přidaný do jeho <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost. Ověřování <xref:System.Xml.XmlReader> objekt se pak použije k vytvoření <xref:System.Xml.XmlDocument> objektu.  
  
 Následující příklad ověří `contosoBooks.xml` sdílené, jak je načten do <xref:System.Xml.XmlDocument> objektu tak, že vytvoříte <xref:System.Xml.XmlDocument> ověřování pomocí <xref:System.Xml.XmlReader> objektu. Vzhledem k tomu, že je platný podle jeho schématu dokumentu XML, vygenerují se upozornění ani chyby ověřování schématu.  
  
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
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad využívá taky `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 V předchozím příkladu <xref:System.Xml.Schema.XmlSchemaValidationException> bude vyvolána při <xref:System.Xml.XmlDocument.Load%2A> je volána, pokud libovolný typ atributu nebo elementu se neshoduje s odpovídající typ zadaný v ověřování schématu. Pokud <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> je nastaven ověřování <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> bude volána pokaždé, když se zjistil se neplatný typ.  
  
 <xref:System.Xml.Schema.XmlSchemaException> Bude vyvolána, pokud atribut nebo element s <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> nastavena na `invalid` přistupuje <xref:System.Xml.XPath.XPathNavigator>.  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Vlastnost lze použít k určení, zda jednotlivé atribut nebo element je platné při přístupu k atributů nebo elementů s <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
>  Po načtení dokumentu XML do <xref:System.Xml.XmlDocument> objekt s přidružené schéma, který definuje výchozí hodnoty <xref:System.Xml.XmlDocument> objekt zpracuje, tyto výchozí hodnoty jako jsou uvedeny v dokumentu XML. To znamená, že <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> vždy vrátí vlastnost `false` pro element, který byl i v případě, že v dokumentu XML byla zapsána jako prázdný element převezme ve schématu.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Ověřování dokumentu pomocí metody ověřování  
 <xref:System.Xml.XmlDocument.Validate%2A> Metodu <xref:System.Xml.XmlDocument> třídy ověří dokumentu XML, který je součástí <xref:System.Xml.XmlDocument> objektu pomocí schémat zadané v <xref:System.Xml.XmlDocument> objektu <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost a provádí informační sadu rozšíření. Výsledkem je dříve netypový kód XML dokumentu v <xref:System.Xml.XmlDocument> objektu nahradí zadaný dokument.  
  
 <xref:System.Xml.XmlDocument> Objekt hlásí chyby ověřování schématu a upozornění pomocí <xref:System.Xml.Schema.ValidationEventHandler> delegát předaný jako parametr <xref:System.Xml.XmlDocument.Validate%2A> metoda.  
  
 Následující příklad ověří `contosoBooks.xml` obsažené v souboru <xref:System.Xml.XmlDocument> objektu proti `contosoBooks.xsd` obsažené ve schématu <xref:System.Xml.XmlDocument> objektu <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost.  
  
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
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad využívá taky `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Ověření úprav  
 Po provedení změny do dokumentu XML, můžete ověřit změny schématu pro používání dokumentu XML <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.  
  
 Následující příklad ověří `contosoBooks.xml` sdílené, jak je načten do <xref:System.Xml.XmlDocument> objektu tak, že vytvoříte <xref:System.Xml.XmlDocument> ověřování pomocí <xref:System.Xml.XmlReader> objektu. Dokument XML proběhne úspěšně, protože je načtena bez generování upozornění ani chyby ověřování schématu. Příklad poté vytvoří dvě změny v dokumentu XML, které jsou neplatné podle `contosoBooks.xsd` schématu. První úpravy vloží neplatný podřízený element výsledkem je chyba ověření schématu a druhý změnu nastaví hodnotu typu uzlu na hodnotu, která je neplatná podle typu uzlu, což vede k výjimce.  
  
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
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad využívá taky `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 V předchozím příkladu se provádí dva úpravy dokumentu XML, který je součástí <xref:System.Xml.XmlDocument> objektu. Jako dokument XML byl načten, žádné chyby ověřování schématu došlo k by byly zpracovány metodu obslužné rutiny události ověření a zapsána do konzoly.  
  
 V tomto příkladu byly zavedeny chyby ověření po dokumentu XML byl načten a našly se pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.  
  
 Změny provedené pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy vedlo <xref:System.InvalidCastException> protože nová hodnota nebyl platný podle schématu typu uzlu.  
  
 Další informace o změně hodnot pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodu, najdete v článku [upravit dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.  
  
### <a name="read-only-validation"></a>Ověřování jen pro čtení  
 <xref:System.Xml.XPath.XPathDocument> Třídy je jen pro čtení, v paměti reprezentace dokumentu XML. Oba <xref:System.Xml.XPath.XPathDocument> třídy a <xref:System.Xml.XmlDocument> vytvoření třídy <xref:System.Xml.XPath.XPathNavigator> objekty k procházení a úpravy dokumentů XML. Protože <xref:System.Xml.XPath.XPathDocument> třídy je třída jen pro čtení, <xref:System.Xml.XPath.XPathNavigator> objekt uživatele vrácený <xref:System.Xml.XPath.XPathDocument> objekty nelze upravit obsažené v dokumentu XML <xref:System.Xml.XPath.XPathDocument> objektu.  
  
 V případě ověřování, můžete vytvořit <xref:System.Xml.XPath.XPathDocument> stejně jako můžete vytvořit objekt <xref:System.Xml.XmlDocument> ověřování pomocí <xref:System.Xml.XmlReader> objektu, jak je popsáno výše v tomto tématu. <xref:System.Xml.XPath.XPathDocument> Objekt ověří dokumentu XML, jako je načtena, ale protože nelze upravit XML data <xref:System.Xml.XPath.XPathDocument> objektu nelze znovu ověřit dokument XML.  
  
 Další informace o jen pro čtení a upravovat <xref:System.Xml.XPath.XPathNavigator> objekty, najdete [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) tématu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Načítání dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [Přístup k datům XML pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [Úpravy dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
