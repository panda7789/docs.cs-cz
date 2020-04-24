---
title: Mapování hierarchie objektů na data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 642a7e5321d0150865f74a66a811914bc9f5d21d
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160024"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a>Mapování hierarchie objektů na data XML
V případě, že je dokument XML v paměti, konceptuální reprezentace je strom. Pro programování máte hierarchii objektů pro přístup k uzlům stromu. Následující příklad ukazuje, jak se obsah XML stávají uzly.  
  
 Jelikož je XML čteno do XML model DOM (Document Object Model) (DOM), části jsou přeloženy do uzlů a tyto uzly uchovávají další metadata o sebe, jako je například typ a hodnoty jejich uzlu. Typ uzlu je jeho objekt a je to, co určuje akce, které lze provést a které vlastnosti lze nastavit nebo načíst.  
  
 Pokud máte následující jednoduchý kód XML:  
  
 **Vstup**  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 Vstup je reprezentován v paměti jako následující strom uzlu s přiřazenou vlastností typu uzlu:  
  
 ![Příklad stromu uzlu](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")  
Reprezentace stromu uzlů v knize a názvu  
  
 `book` Prvek se stala objektem **XmlElement** , další prvek `title`se také stal atributem **XmlElement**, zatímco obsah elementu se stala objektem **XmlText** . Při prohlížení metod a vlastností třídy **XmlElement** se metody a vlastnosti liší od metod a vlastností dostupných v objektu **XmlText** . Proto si poznáte, jaký typ uzlu se kód XML stává zásadní, protože jeho typ uzlu určuje akce, které lze provést.  
  
 Následující příklad přečte v datech XML a zapisuje jiný text v závislosti na typu uzlu. Použijte následující datový soubor XML jako Input, **Items. XML**:  
  
 **Vstup**  
  
```xml  
<?xml version="1.0"?>  
<!-- This is a sample XML document -->  
<!DOCTYPE Items [<!ENTITY number "123">]>  
<Items>  
  <Item>Test with an entity: &number;</Item>  
  <Item>test with a child element <more/> stuff</Item>  
  <Item>test with a CDATA section <![CDATA[<456>]]> def</Item>  
  <Item>Test with a char entity: A</Item>  
  <!-- Fourteen chars in this element.-->  
  <Item>1234567890ABCD</Item>  
</Items>  
```  
  
 Následující příklad kódu přečte soubor **Items. XML** a zobrazí informace pro každý typ uzlu.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
    Private Const filename As String = "items.xml"  
  
    Public Shared Sub Main()  
  
        Dim reader As XmlTextReader = Nothing  
  
        Try  
            ' Load the reader with the data file and
            'ignore all white space nodes.
            reader = New XmlTextReader(filename)  
            reader.WhitespaceHandling = WhitespaceHandling.None  
  
            ' Parse the file and display each of the nodes.  
            While reader.Read()  
                Select Case reader.NodeType  
                    Case XmlNodeType.Element  
                        Console.Write("<{0}>", reader.Name)  
                    Case XmlNodeType.Text  
                        Console.Write(reader.Value)  
                    Case XmlNodeType.CDATA  
                        Console.Write("<![CDATA[{0}]]>", reader.Value)  
                    Case XmlNodeType.ProcessingInstruction  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value)  
                    Case XmlNodeType.Comment  
                        Console.Write("<!--{0}-->", reader.Value)  
                    Case XmlNodeType.XmlDeclaration  
                        Console.Write("<?xml version='1.0'?>")  
                    Case XmlNodeType.Document  
                    Case XmlNodeType.DocumentType  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value)  
                    Case XmlNodeType.EntityReference  
                        Console.Write(reader.Name)  
                    Case XmlNodeType.EndElement  
                        Console.Write("</{0}>", reader.Name)  
                End Select  
            End While  
  
        Finally  
            If Not (reader Is Nothing) Then  
                reader.Close()  
            End If  
        End Try  
    End Sub 'Main ' End class  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    private const String filename = "items.xml";  
  
    public static void Main()  
    {  
        XmlTextReader reader = null;  
  
        try  
        {  
            // Load the reader with the data file and ignore
            // all white space nodes.  
            reader = new XmlTextReader(filename);  
            reader.WhitespaceHandling = WhitespaceHandling.None;  
  
            // Parse the file and display each of the nodes.  
            while (reader.Read())  
            {  
                switch (reader.NodeType)  
                {  
                    case XmlNodeType.Element:  
                        Console.Write("<{0}>", reader.Name);  
                        break;  
                    case XmlNodeType.Text:  
                        Console.Write(reader.Value);  
                        break;  
                    case XmlNodeType.CDATA:  
                        Console.Write("<![CDATA[{0}]]>", reader.Value);  
                        break;  
                    case XmlNodeType.ProcessingInstruction:  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.Comment:  
                        Console.Write("<!--{0}-->", reader.Value);  
                        break;  
                    case XmlNodeType.XmlDeclaration:  
                        Console.Write("<?xml version='1.0'?>");  
                        break;  
                    case XmlNodeType.Document:  
                        break;  
                    case XmlNodeType.DocumentType:  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.EntityReference:  
                        Console.Write(reader.Name);  
                        break;  
                    case XmlNodeType.EndElement:  
                        Console.Write("</{0}>", reader.Name);  
                        break;  
                }  
            }  
        }  
  
        finally  
        {  
            if (reader != null)  
                reader.Close();  
        }  
    }  
} // End class  
```  
  
 Výstup z příkladu odhalí mapování dat na typy uzlů.  
  
 **Výstup**  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 Přebírání jednoho řádku a použití výstupu vygenerovaného z kódu, můžete použít následující tabulku k analýze, který test uzlu vygeneroval, které řádky výstupu, a tím i informace o tom, jaká data XML se staly typem typu uzlu.  
  
|Vstup|Výstup|Test typu uzlu|  
|-----------|------------|--------------------|  
|\<? XML Version = "1.0"? >|\<? XML verze = ' 1.0 '? >|XmlNodeType. XmlDeclaration|  
|\<!--Toto je ukázkový dokument XML-->|\<!--Toto je ukázkový dokument XML-->|XmlNodeType. Comment|  
|\<! Položky DOCTYPE [\<! Číslo ENTITY "123" >] >|\<! Položky DOCTYPE [\<! Číslo ENTITY "123" >]|XmlNodeType. DocumentType|  
|\<> položek|\<> položek|XmlNodeType. element|  
|\<> položky|\<> položky|XmlNodeType. element|  
|Test s entitou:&number;|Test s entitou: 123|XmlNodeType. text|  
|\</Item>|\</Item>|XmlNodeType. EndElement|  
|\<> položky|\<> položky|XmNodeType. element|  
|test s podřízeným elementem|test s podřízeným elementem|XmlNodeType. text|  
|\<Další>|\<Další>|XmlNodeType. element|  
|vhodné|vhodné|XmlNodeType. text|  
|\</Item>|\</Item>|XmlNodeType. EndElement|  
|\<> položky|\<> položky|XmlNodeType. element|  
|testování pomocí oddílu CDATA|testování pomocí oddílu CDATA|XmlTest. text|  
|<! [CDATA [\<456>]]\>|<! [CDATA [\<456>]]\>|XmlTest. CDATA|  
|IME|IME|XmlNodeType. text|  
|\</Item>|\</Item>|XmlNodeType. EndElement|  
|\<> položky|\<> položky|XmlNodeType. element|  
|Test s entitou char: &\#65;|Test s entitou char: A|XmlNodeType. text|  
|\</Item>|\</Item>|XmlNodeType. EndElement|  
|\<V tomto elementu!--čtrnáct znaků.-->|\<--Čtrnáct znaků v tomto elementu.-->|XmlNodeType. Comment|  
|\<> položky|\<> položky|XmlNodeType. element|  
|1234567890ABCD|1234567890ABCD|XmlNodeType. text|  
|\</Item>|\</Item>|XmlNodeType. EndElement|  
|\</Items>|\</Items>|XmlNodeType. EndElement|  
  
 Musíte znát typ uzlu, který je přiřazen, protože typ uzlu řídí, jaké druhy akcí jsou platné a jaký druh vlastností lze nastavit a načíst.  
  
 Vytváření uzlů pro prázdné znaky je řízeno při načtení dat do modelu DOM příznakem **PreserveWhitespace** . Další informace naleznete v tématu [mezera a významná manipulace s prázdným znakem při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).  
  
 Chcete-li přidat nové uzly do modelu DOM, přečtěte si téma [vkládání uzlů do dokumentu XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md). Chcete-li odebrat uzly z modelu DOM, přečtěte si téma [Odebrání uzlů, obsahu a hodnot z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md). Chcete-li upravit obsah uzlů v modelu DOM, přečtěte si téma [Úprava uzlů, obsahu a hodnot v dokumentu XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
