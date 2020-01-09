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
# <a name="schema-validation-using-xpathnavigator"></a>Ověření schématu pomocí XPathNavigator
Pomocí třídy <xref:System.Xml.XmlDocument> lze ověřit obsah XML obsažený v objektu <xref:System.Xml.XmlDocument> dvěma způsoby. Prvním způsobem je ověřit obsah XML pomocí ověřování objektu <xref:System.Xml.XmlReader> a druhým způsobem je použít metodu <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>. Pomocí třídy <xref:System.Xml.XPath.XPathDocument> můžete také provádět ověřování obsahu XML jen pro čtení.  
  
## <a name="validating-xml-data"></a>Ověřování dat XML  
 Třída <xref:System.Xml.XmlDocument> neověřuje dokument XML pomocí standardu DTD nebo schématu XSD (XML Schema Definition Language). Ověřuje pouze to, zda je dokument XML ve správném formátu.  
  
 Prvním způsobem, jak ověřit dokument XML, je ověřit dokument tak, jak je načten do objektu <xref:System.Xml.XmlDocument> pomocí ověřování objektu <xref:System.Xml.XmlReader>. Druhým způsobem je ověřit dříve Netypový dokument XML pomocí metody <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>. V obou případech lze změny ověřeného dokumentu XML znovu ověřit pomocí metody <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Ověřování dokumentu při jeho načtení  
 Ověřování objektu <xref:System.Xml.XmlReader> je vytvořeno předáním objektu <xref:System.Xml.XmlReaderSettings> do metody <xref:System.Xml.XmlReader.Create%2A> třídy <xref:System.Xml.XmlReader>, která přebírá objekt <xref:System.Xml.XmlReaderSettings> jako parametr. Objekt <xref:System.Xml.XmlReaderSettings> předaný jako parametr má vlastnost <xref:System.Xml.XmlReaderSettings.ValidationType%2A> nastavenou na `Schema` a schéma XML pro dokument XML obsažený v objektu <xref:System.Xml.XmlDocument> přidaného do jeho <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnosti. K vytvoření objektu <xref:System.Xml.XmlDocument> se pak použije ověřování objektu <xref:System.Xml.XmlReader>.  
  
 Následující příklad ověřuje `contosoBooks.xml` soubor tak, jak je načten do objektu <xref:System.Xml.XmlDocument> vytvořením objektu <xref:System.Xml.XmlDocument> pomocí ověřování objektu <xref:System.Xml.XmlReader>. Vzhledem k tomu, že dokument XML je podle jeho schématu platný, nejsou generovány žádné chyby ověřování schématu ani upozornění.  
  
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
  
 Příklad přebírá soubor `contosoBooks.xml` jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Příklad také přebírá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 V předchozím příkladu se <xref:System.Xml.Schema.XmlSchemaValidationException> vyvolá při volání <xref:System.Xml.XmlDocument.Load%2A>, pokud jakýkoli typ atributu nebo elementu neodpovídá odpovídajícímu typu zadanému v ověřovacím schématu. Pokud je pro ověřování <xref:System.Xml.XmlReader>nastavena <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> bude volána vždy, když dojde k neplatnému typu.  
  
 <xref:System.Xml.Schema.XmlSchemaException> bude vyvolána, pokud k atributu nebo elementu s <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> nastaveným na `invalid` má <xref:System.Xml.XPath.XPathNavigator>k dispozici.  
  
 Vlastnost <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> lze použít k určení, zda je nebo není jednotlivý atribut nebo element platný při přístupu k atributům nebo prvkům s <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
> Při načtení dokumentu XML do objektu <xref:System.Xml.XmlDocument> s přidruženým schématem, které definuje výchozí hodnoty, objekt <xref:System.Xml.XmlDocument> zpracovává tyto výchozí hodnoty, jako by se zobrazily v dokumentu XML. To znamená, že vlastnost <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> vždy vrátí `false` pro prvek, který byl nastaven jako výchozí ve schématu, i v případě, že v dokumentu XML byl zapsán jako prázdný prvek.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Ověření dokumentu pomocí metody Validate  
 Metoda <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument> ověřuje dokument XML obsažený v objektu <xref:System.Xml.XmlDocument> proti schématům zadaným ve vlastnosti <xref:System.Xml.XmlDocument.Schemas%2A> objektu <xref:System.Xml.XmlDocument> a provádí rozšíření informačního souboru. Výsledkem je dříve Netypový dokument XML v objektu <xref:System.Xml.XmlDocument> nahrazený typovým dokumentem.  
  
 Objekt <xref:System.Xml.XmlDocument> hlásí chyby ověřování schématu a upozornění pomocí <xref:System.Xml.Schema.ValidationEventHandler> delegáta předaného jako parametr metodě <xref:System.Xml.XmlDocument.Validate%2A>.  
  
 Následující příklad ověří `contosoBooks.xml` soubor obsažený v objektu <xref:System.Xml.XmlDocument> proti schématu `contosoBooks.xsd` obsaženému ve vlastnosti <xref:System.Xml.XmlDocument.Schemas%2A> objektu <xref:System.Xml.XmlDocument>.  
  
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
  
 Příklad přebírá soubor `contosoBooks.xml` jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Příklad také přebírá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Ověřování změn  
 Po provedení úprav dokumentu XML můžete ověřit změny schématu pro dokument XML pomocí metody <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>.  
  
 Následující příklad ověřuje `contosoBooks.xml` soubor tak, jak je načten do objektu <xref:System.Xml.XmlDocument> vytvořením objektu <xref:System.Xml.XmlDocument> pomocí ověřování objektu <xref:System.Xml.XmlReader>. Dokument XML se úspěšně ověřuje, protože je načtený bez generování chyb nebo upozornění ověřování schématu. Příklad následně provede dvě úpravy dokumentu XML, které jsou podle schématu `contosoBooks.xsd` neplatné. První změna vloží neplatný podřízený element, který má za následek chybu ověřování schématu a druhá změna nastaví hodnotu typovaného uzlu na hodnotu, která je neplatná podle typu uzlu, který je výsledkem výjimky.  
  
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
  
 Příklad přebírá soubor `contosoBooks.xml` jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Příklad také přebírá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 V předchozím příkladu jsou provedeny dvě úpravy dokumentu XML obsaženého v objektu <xref:System.Xml.XmlDocument>. Jak byl načten dokument XML, jakékoli zjištěné chyby ověřování schématu by byly zpracovány metodou obslužné rutiny události ověřování a zapsány do konzoly.  
  
 V tomto příkladu byly chyby ověřování představeny po načtení dokumentu XML a byly nalezeny pomocí metody <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>.  
  
 Změny provedené pomocí metody <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> třídy <xref:System.Xml.XPath.XPathNavigator> způsobily <xref:System.InvalidCastException>, protože nová hodnota byla podle typu schématu uzlu neplatná.  
  
 Další informace o úpravách hodnot pomocí metody <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> naleznete v tématu [Úprava dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .  
  
### <a name="read-only-validation"></a>Ověřování jen pro čtení  
 Třída <xref:System.Xml.XPath.XPathDocument> je reprezentace dokumentu XML, která je jen pro čtení. Třída <xref:System.Xml.XPath.XPathDocument> i třída <xref:System.Xml.XmlDocument> vytvářejí objekty <xref:System.Xml.XPath.XPathNavigator> pro procházení a úpravy dokumentů XML. Vzhledem k tomu, že třída <xref:System.Xml.XPath.XPathDocument> je třída, která je jen pro čtení, vrácený objekt <xref:System.Xml.XPath.XPathNavigator> objektů <xref:System.Xml.XPath.XPathDocument> nemůže upravovat dokument XML obsažený v objektu <xref:System.Xml.XPath.XPathDocument>.  
  
 V případě ověřování můžete vytvořit objekt <xref:System.Xml.XPath.XPathDocument> stejným způsobem jako objekt <xref:System.Xml.XmlDocument> pomocí ověřování <xref:System.Xml.XmlReader> objektu, jak je popsáno výše v tomto tématu. Objekt <xref:System.Xml.XPath.XPathDocument> ověří dokument XML, jak je načten, ale vzhledem k tomu, že data XML nelze upravovat v objektu <xref:System.Xml.XPath.XPathDocument>, nelze znovu ověřit dokument XML.  
  
 Další informace o objektech jen pro čtení a upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů najdete v tématu věnovaném [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) .  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Načítání dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [Přístup k datům XML pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [Úpravy dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
