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
# <a name="schema-validation-using-xpathnavigator"></a>Ověření schématu pomocí objektem XPathNavigator nastaveným na
Pomocí <xref:System.Xml.XmlDocument> třídu, můžete ověřit obsah XML, který je součástí <xref:System.Xml.XmlDocument> objektu dvěma způsoby. První způsob je ověřit obsah XML pomocí ověřování <xref:System.Xml.XmlReader> objekt a druhým způsobem je použití <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy. Můžete také provést jen pro čtení ověření obsahu pomocí XML <xref:System.Xml.XPath.XPathDocument> třídy.  
  
## <a name="validating-xml-data"></a>Ověřování dat XML  
 <xref:System.Xml.XmlDocument> Třída neověřuje dokument XML pomocí DTD nebo XML schéma ověřování schématu definition language (XSD) ve výchozím nastavení. Pouze ověřuje, zda je v dokumentu XML správně vytvořen.  
  
 První způsob, jak ověřit dokument XML je k ověření dokumentu, jako je načten do <xref:System.Xml.XmlDocument> pomocí ověřování <xref:System.Xml.XmlReader> objektu. Druhý způsob je ověřit dříve bez typu dokumentu XML pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy. V obou případech může být obnoveny změny ověřené dokument XML, pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Ověřování dokumentu po načtení  
 Ověření <xref:System.Xml.XmlReader> předáním je vytvořen objekt <xref:System.Xml.XmlReaderSettings> do objektu <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídu, která přebírá <xref:System.Xml.XmlReaderSettings> objektu jako parametr. <xref:System.Xml.XmlReaderSettings> Objekt předaný parametr má <xref:System.Xml.XmlReaderSettings.ValidationType%2A> vlastnost nastavena na hodnotu `Schema` a schéma XML pro dokument XML, které jsou součástí <xref:System.Xml.XmlDocument> objekt přidaný do jeho <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost. Ověřování <xref:System.Xml.XmlReader> objekt se pak používá k vytvoření <xref:System.Xml.XmlDocument> objektu.  
  
 V následujícím příkladu ověří `contosoBooks.xml` souborů, jako je načten do <xref:System.Xml.XmlDocument> objekt vytvořením <xref:System.Xml.XmlDocument> pomocí ověřování <xref:System.Xml.XmlReader> objektu. Vzhledem k tomu, že v dokumentu XML není platná podle jeho schématu, jsou generovány žádné chyby ověřování schématu nebo upozornění.  
  
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
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad také trvá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 V předchozím příkladu <xref:System.Xml.Schema.XmlSchemaValidationException> bude vyvolána při <xref:System.Xml.XmlDocument.Load%2A> je volána, pokud žádný typ elementu nebo atributu neodpovídá odpovídající typ zadaný v ověřování schématu. Pokud <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> je nastavený na ověřování <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> bude zavolána vždy, když se zjistil neplatný typ.  
  
 <xref:System.Xml.Schema.XmlSchemaException> Bude vyvolána, pokud atribut nebo element s <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> nastavena na `invalid` přistupuje <xref:System.Xml.XPath.XPathNavigator>.  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Vlastnost lze použít k určení, zda jednotlivé atribut nebo element je platný při přístupu k atributy nebo elementů pomocí <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
>  Když je dokument XML načten do <xref:System.Xml.XmlDocument> objekt s přidružené schéma, která definuje výchozí hodnoty <xref:System.Xml.XmlDocument> objekt zpracovává tato výchozí nastavení, jako kdyby byly zobrazeny v dokumentu XML. To znamená, že <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> vlastnost vždy vrátí hodnotu `false` pro element, který byl převezme z schématu, i když v dokumentu XML byla zapsána jako prázdný element.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Ověřování dokumentu s použitím metoda ověření  
 <xref:System.Xml.XmlDocument.Validate%2A> Metodu <xref:System.Xml.XmlDocument> třída ověří obsažené v dokumentu XML <xref:System.Xml.XmlDocument> pomocí schémat zadaný v objektu <xref:System.Xml.XmlDocument> objektu <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost a provede informační sadu rozšíření. Výsledkem je dříve bez typu dokumentu XML v <xref:System.Xml.XmlDocument> objektu nahradí typu dokumentu.  
  
 <xref:System.Xml.XmlDocument> Objekt sestavy chyby ověřování schématu a upozornění pomocí <xref:System.Xml.Schema.ValidationEventHandler> delegáta předány jako parametr, který se <xref:System.Xml.XmlDocument.Validate%2A> metoda.  
  
 Následující příklad ověří `contosoBooks.xml` obsažené v souboru <xref:System.Xml.XmlDocument> objektu proti `contosoBooks.xsd` schématu obsažené v <xref:System.Xml.XmlDocument> objektu <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost.  
  
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
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad také trvá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Ověření úprav  
 Po úprav dokumentu XML, můžete ověřit změny pro schéma pro dokument XML pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.  
  
 V následujícím příkladu ověří `contosoBooks.xml` souborů, jako je načten do <xref:System.Xml.XmlDocument> objekt vytvořením <xref:System.Xml.XmlDocument> pomocí ověřování <xref:System.Xml.XmlReader> objektu. V dokumentu XML je úspěšně ověřit, protože je načten bez generování všechny chyby ověřování schématu nebo upozornění. V příkladu potom vytvoří dvě změny v dokumentu XML, které jsou neplatné podle `contosoBooks.xsd` schématu. První úpravy vloží neplatným podřízeným elementem výsledkem je chyba ověření schématu a druhý úpravy nastaví hodnota typu uzlu na hodnotu, která je neplatná závislosti na typu uzlu, což vede k výjimce.  
  
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
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad také trvá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 V předchozím příkladu dvě změny provedené v dokumentu XML, které jsou součástí <xref:System.Xml.XmlDocument> objektu. Jako dokument XML byl načten, všechny chyby ověřování schématu došlo by byly zpracovávaných obslužná rutina události ověření a zapsána do konzoly.  
  
 V tomto příkladu byly zavedeny chyby ověření po dokumentu XML bylo načteno a nebyly nalezeny pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.  
  
 Změny provedené pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třída výsledkem <xref:System.InvalidCastException> kvůli neplatnosti podle schématu typ uzlu novou hodnotu.  
  
 Další informace o změnách pomocí hodnot <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodu, najdete v části [upravit Data XML pomocí objektem XPathNavigator nastaveným](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.  
  
### <a name="read-only-validation"></a>Ověření jen pro čtení  
 <xref:System.Xml.XPath.XPathDocument> Třída je jen pro čtení, v paměti reprezentace dokument XML. Obě <xref:System.Xml.XPath.XPathDocument> – třída a <xref:System.Xml.XmlDocument> vytvořit třídu <xref:System.Xml.XPath.XPathNavigator> objektů přejděte a úpravám dokumentů XML. Protože <xref:System.Xml.XPath.XPathDocument> třídy je třída jen pro čtení, <xref:System.Xml.XPath.XPathNavigator> je vrácen objekt z <xref:System.Xml.XPath.XPathDocument> objekty obsažené v dokumentu XML nelze upravit, <xref:System.Xml.XPath.XPathDocument> objektu.  
  
 V případě ověření, můžete vytvořit <xref:System.Xml.XPath.XPathDocument> objektu stejně jako vytvoříte <xref:System.Xml.XmlDocument> pomocí ověřování <xref:System.Xml.XmlReader> objektu, jak je popsáno výše v tomto tématu. <xref:System.Xml.XPath.XPathDocument> Objekt ověří dokumentu XML, jako je načtena, ale protože data XML v nelze upravit <xref:System.Xml.XPath.XPathDocument> objektu nelze znovu ověřit v dokumentu XML.  
  
 Další informace o jen pro čtení a upravovat <xref:System.Xml.XPath.XPathNavigator> objekty, najdete [čtení dat XML pomocí XPathDocument třídou XMLDocument nastavenou na](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) tématu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování kódu XML dat pomocí jazyka XPath datový Model](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Načítání dat XML pomocí XPathDocument a třídou XMLDocument nastavenou na](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [Výběr, Evaluating a porovnávání dat XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [Přístup k datům XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [Úpravy pomocí objektem XPathNavigator nastaveným na Data XML](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
