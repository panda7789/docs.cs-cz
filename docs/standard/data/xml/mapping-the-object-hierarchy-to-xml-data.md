---
title: Mapování hierarchie objektů na data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1808121049c6344b72b1c9d99e19c46422dfa0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650282"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a>Mapování hierarchie objektů na data XML
Když je dokument XML v paměti, koncepční reprezentace je strom. Pro programování, můžete mít hierarchii objektů pro přístup k uzly stromu. Následující příklad ukazuje, jak obsah XML stane uzly.  
  
 XML je pro čtení do XML Document Object Model (DOM), kusy jsou přeloženy do uzlů a další metadata o samotné, jako je například jejich typ uzlu a hodnoty uchovávat tyto uzly. Typ uzlu je její objekt a co určuje, jaké akce lze provádět a které vlastnosti můžete nastavit nebo načíst.  
  
 Pokud máte následující jednoduchý kód XML:  
  
 **Vstup**  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 Vstup je vyjádřena v paměti jako následující uzel stromu s vlastností typu přiřazeném uzlu:  
  
 ![Příklad uzlu stromu](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")  
Knihy a název reprezentace uzlu stromu  
  
 `book` Prvek stane **XmlElement** objektu, další prvek `title`, stane **XmlElement**, přestože obsah elementu se stane **XmlText** objektu. V podíváme **XmlElement** metody a vlastnosti, metody a vlastnosti, které se liší od metody a vlastnosti, které jsou k dispozici na **XmlText** objektu. Takže vědět, jaký typ uzlu, bude kód XML je důležité, protože jeho typ uzlu určuje akce, které lze provést.  
  
 Následující příklad načte v datech XML a zapíše jiný text, v závislosti na typu uzlu. Pomocí následujících datového souboru XML jako vstup, **items.xml**:  
  
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
  
 Následující příklad čte kód **items.xml** soubor a zobrazí informace pro každý typ uzlu.  
  
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
  
 Výstup z příkladu zobrazí mapování dat na typy uzlů.  
  
 **Output**  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 Trvá jeden vstup najednou a používání výstup generovaný z kódu, můžete analyzovat, jaké test uzlu vygeneruje výstup, které řádky a vysvětlení, jaká data XML začal být jaký druh typu uzlu v následující tabulce.  
  
|Vstup|Výstup|Test typ uzlu|  
|-----------|------------|--------------------|  
|\<? xml verze = "1.0"? >|\<? xml verze = "1.0'? >|XmlNodeType.XmlDeclaration|  
|\<! – Toto je ukázkový dokument XML-->|\<! – Toto je ukázkový dokument XML-->|XmlNodeType.Comment|  
|\<! Typ dokumentu položky [\<! Počet ENTIT "123" >] >|\<! Typ dokumentu položky [\<! Počet ENTIT "123" >]|XmlNodeType.DocumentType|  
|\<Položky >|\<Položky >|XmlNodeType.Element|  
|\<Položka >|\<Položka >|XmlNodeType.Element|  
|Testování s převodem entity: &number;|Testování s převodem entity: 123|XmlNodeType.Text|  
|\</ Položka >|\</ Položka >|XmlNodeType.EndElement|  
|\<Položka >|\<Položka >|XmNodeType.Element|  
|testování s podřízeným elementem|testování s podřízeným elementem|XmlNodeType.Text|  
|\<Další >|\<Další >|XmlNodeType.Element|  
|věci|věci|XmlNodeType.Text|  
|\</ Položka >|\</ Položka >|XmlNodeType.EndElement|  
|\<Položka >|\<Položka >|XmlNodeType.Element|  
|testování pomocí sekce CDATA|testování pomocí sekce CDATA|XmlTest.Text|  
|<![CDATA[\<456>]]\>|<![CDATA[\<456>]]\>|XmlTest.CDATA|  
|DEF|DEF|XmlNodeType.Text|  
|\</ Položka >|\</ Položka >|XmlNodeType.EndElement|  
|\<Položka >|\<Položka >|XmlNodeType.Element|  
|Test s entitou char: &\#65;|Testování s char entity: OBJEKT|XmlNodeType.Text|  
|\</ Položka >|\</ Položka >|XmlNodeType.EndElement|  
|\<! –--> Čtrnáct znaky v tomto elementu.|\<----> Čtrnáct znaky v tomto elementu.|XmlNodeType.Comment|  
|\<Položka >|\<Položka >|XmlNodeType.Element|  
|1234567890ABCD|1234567890ABCD|XmlNodeType.Text|  
|\</ Položka >|\</ Položka >|XmlNodeType.EndElement|  
|\</ Položky >|\</ Položky >|XmlNodeType.EndElement|  
  
 Musíte vědět, jaký typ uzlu je přiřazen, jako uzel typ řídí, jaké druhy akce jsou platná a jaký druh vlastnosti můžete nastavit a načíst.  
  
 Vytvoření uzlu pro prázdné místo je řízena, když data se načtou do modelu DOM pomocí **PreserveWhitespace** příznak. Další informace najdete v tématu [mezer a významných mezer zpracování při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).  
  
 Přidání nových uzlů v modelu DOM naleznete v tématu [vkládání uzlů do dokumentu XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md). Na odebrání uzlů z modelu DOM, naleznete v tématu [odebrání uzlů, obsahu a hodnot z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md). Pokud chcete upravit obsah uzlů v modelu DOM, naleznete v tématu [úprava uzlů, obsahu a hodnot v dokumentu XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
