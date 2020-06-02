---
title: Ověření schématu pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: f6e56616543bf7d2ad2e6be4d7bf7cbc50ba3a23
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292004"
---
# <a name="schema-validation-using-xpathnavigator"></a>Ověření schématu pomocí XPathNavigator
Pomocí <xref:System.Xml.XmlDocument> třídy můžete ověřit obsah XML obsažený v <xref:System.Xml.XmlDocument> objektu dvěma způsoby. Prvním způsobem je ověřit obsah XML pomocí ověřování <xref:System.Xml.XmlReader> objektu a druhým způsobem je použít <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy. Můžete také provést ověřování obsahu XML jen pro čtení pomocí <xref:System.Xml.XPath.XPathDocument> třídy.  
  
## <a name="validating-xml-data"></a>Ověřování dat XML  
 <xref:System.Xml.XmlDocument>Třída neověřuje dokument XML buď pomocí ověřování schématu DTD, nebo XML schématu Definition Language (XSD) ve výchozím nastavení. Ověřuje pouze to, zda je dokument XML ve správném formátu.  
  
 Prvním způsobem, jak ověřit dokument XML, je ověřit dokument tak, jak je načten do <xref:System.Xml.XmlDocument> objektu pomocí ověřování <xref:System.Xml.XmlReader> objektu. Druhým způsobem je ověřit dříve Netypový dokument XML pomocí <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> třídy. V obou případech lze změny ověřeného dokumentu XML znovu ověřit pomocí <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> třídy.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Ověřování dokumentu při jeho načtení  
 Ověřování <xref:System.Xml.XmlReader> objektu je vytvořeno předáním <xref:System.Xml.XmlReaderSettings> objektu <xref:System.Xml.XmlReader.Create%2A> metodě <xref:System.Xml.XmlReader> třídy, která přebírá <xref:System.Xml.XmlReaderSettings> objekt jako parametr. <xref:System.Xml.XmlReaderSettings>Objekt předaný jako parametr má <xref:System.Xml.XmlReaderSettings.ValidationType%2A> vlastnost nastavenou na `Schema` a schéma XML pro dokument XML obsažený v <xref:System.Xml.XmlDocument> objektu přidaném do <xref:System.Xml.XmlReaderSettings.Schemas%2A> Vlastnosti. Objekt ověřování <xref:System.Xml.XmlReader> se pak použije k vytvoření <xref:System.Xml.XmlDocument> objektu.  
  
 Následující příklad ověřuje `contosoBooks.xml` soubor tak, jak je načten do <xref:System.Xml.XmlDocument> objektu vytvořením <xref:System.Xml.XmlDocument> objektu pomocí ověřování <xref:System.Xml.XmlReader> objektu. Vzhledem k tomu, že dokument XML je podle jeho schématu platný, nejsou generovány žádné chyby ověřování schématu ani upozornění.  
  
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
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Příklad také přebírá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 V předchozím příkladu <xref:System.Xml.Schema.XmlSchemaValidationException> bude vyvolána výjimka, když <xref:System.Xml.XmlDocument.Load%2A> je volána, pokud jakýkoli typ atributu nebo elementu neodpovídá odpovídajícímu typu zadanému v rámci ověřování schématu. Pokud <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> je nastavena při ověřování <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> bude vyvolána při každém zjištění neplatného typu.  
  
 <xref:System.Xml.Schema.XmlSchemaException>Bude vyvolána, pokud je k atributu nebo elementu s <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> nastavenou vlastností `invalid` přistupovaná pomocí <xref:System.Xml.XPath.XPathNavigator> .  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A>Vlastnost lze použít k určení, zda je jednotlivý atribut nebo element platný při přístupu k atributům nebo prvkům s <xref:System.Xml.XPath.XPathNavigator> .  
  
> [!NOTE]
> Při načtení dokumentu XML do <xref:System.Xml.XmlDocument> objektu s přidruženým schématem, které definuje výchozí hodnoty, <xref:System.Xml.XmlDocument> objekt zpracovává tyto výchozí hodnoty, jako by se zobrazily v dokumentu XML. To znamená, že <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> vlastnost vždy vrátí `false` pro prvek, který byl nastaven jako výchozí ve schématu, i v případě, že v dokumentu XML byl zapsán jako prázdný prvek.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Ověření dokumentu pomocí metody Validate  
 <xref:System.Xml.XmlDocument.Validate%2A>Metoda <xref:System.Xml.XmlDocument> třídy OVĚŘÍ dokument XML obsažený v <xref:System.Xml.XmlDocument> objektu proti schématům zadaným ve <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> vlastnosti objektu a provede rozšíření informačního souboru. Výsledkem je dříve Netypový dokument XML v <xref:System.Xml.XmlDocument> objektu nahrazený typovým dokumentem.  
  
 <xref:System.Xml.XmlDocument>Objekt hlásí chyby ověřování schématu a upozornění pomocí <xref:System.Xml.Schema.ValidationEventHandler> delegáta předaného jako parametru <xref:System.Xml.XmlDocument.Validate%2A> metodě.  
  
 Následující příklad ověří `contosoBooks.xml` soubor obsažený v <xref:System.Xml.XmlDocument> objektu proti `contosoBooks.xsd` schématu obsaženému ve <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> vlastnosti objektu.  
  
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
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Příklad také přebírá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Ověřování změn  
 Po provedení úprav dokumentu XML můžete ověřit změny schématu pro dokument XML pomocí <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> třídy.  
  
 Následující příklad ověřuje `contosoBooks.xml` soubor tak, jak je načten do <xref:System.Xml.XmlDocument> objektu vytvořením <xref:System.Xml.XmlDocument> objektu pomocí ověřování <xref:System.Xml.XmlReader> objektu. Dokument XML se úspěšně ověřuje, protože je načtený bez generování chyb nebo upozornění ověřování schématu. Příklad následně provede dvě úpravy dokumentu XML, které jsou podle `contosoBooks.xsd` schématu neplatné. První změna vloží neplatný podřízený element, který má za následek chybu ověřování schématu a druhá změna nastaví hodnotu typovaného uzlu na hodnotu, která je neplatná podle typu uzlu, který je výsledkem výjimky.  
  
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
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Příklad také přebírá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 V předchozím příkladu jsou provedeny dvě úpravy dokumentu XML obsaženého v <xref:System.Xml.XmlDocument> objektu. Jak byl načten dokument XML, jakékoli zjištěné chyby ověřování schématu by byly zpracovány metodou obslužné rutiny události ověřování a zapsány do konzoly.  
  
 V tomto příkladu byly chyby ověřování představeny po načtení dokumentu XML a byly nalezeny pomocí <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> třídy.  
  
 Změny provedené pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy způsobily výjimku, <xref:System.InvalidCastException> protože nová hodnota byla podle typu schématu uzlu neplatná.  
  
 Další informace o úpravách hodnot pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody naleznete v tématu [Úprava dat XML pomocí XPathNavigator](modify-xml-data-using-xpathnavigator.md) .  
  
### <a name="read-only-validation"></a>Ověřování jen pro čtení  
 <xref:System.Xml.XPath.XPathDocument>Třída je reprezentace dokumentu XML, která je určena jen pro čtení, v paměti. <xref:System.Xml.XPath.XPathDocument>Třída i <xref:System.Xml.XmlDocument> třída vytváří <xref:System.Xml.XPath.XPathNavigator> objekty pro navigaci a úpravy dokumentů XML. Vzhledem k tomu <xref:System.Xml.XPath.XPathDocument> , že třída je třída, která je jen pro čtení, <xref:System.Xml.XPath.XPathNavigator> objekt vrácený z <xref:System.Xml.XPath.XPathDocument> objektů nemůže upravovat dokument XML obsažený v <xref:System.Xml.XPath.XPathDocument> objektu.  
  
 V případě ověřování můžete vytvořit <xref:System.Xml.XPath.XPathDocument> objekt stejně jako <xref:System.Xml.XmlDocument> objekt pomocí ověřování <xref:System.Xml.XmlReader> objektu, jak je popsáno výše v tomto tématu. <xref:System.Xml.XPath.XPathDocument>Objekt ověří dokument XML, jak je načten, ale vzhledem k tomu, že nelze upravovat data XML v <xref:System.Xml.XPath.XPathDocument> objektu, nelze znovu ověřit dokument XML.  
  
 Další informace o objektech jen pro čtení a upravitelných <xref:System.Xml.XPath.XPathNavigator> objektech naleznete v tématu věnovaném [čtení dat XML pomocí XPathDocument a XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md) .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](process-xml-data-using-the-xpath-data-model.md)
- [Načítání dat XML pomocí XPathDocument a XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [Přístup k datům XML pomocí XPathNavigator](accessing-xml-data-using-xpathnavigator.md)
- [Úpravy dat XML pomocí XPathNavigator](editing-xml-data-using-xpathnavigator.md)
