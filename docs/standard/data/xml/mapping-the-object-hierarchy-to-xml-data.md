---
title: Mapování hierarchie objektů na XML Data
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45f39701d409ba76e3c3f428f484b6fd5e538fbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577199"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a>Mapování hierarchie objektů na XML Data
Když je dokument XML v paměti, je koncepční reprezentace stromu. Pro programování, nebudete mít hierarchii k objektu pro přístup k uzlu stromu. Následující příklad ukazuje, jak se změní obsah XML na uzly.  
  
 Soubor XML je pro čtení do XML modelu DOM (Document Object), jsou převedeny na požadované do uzlů a tyto uzly ukládat další metadata o sami, například jejich typ uzlu a hodnoty. Typ uzlu je jeho objekt a je co určuje, jaké akce lze provést a co vlastnosti nelze nastavit ani načíst.  
  
 Pokud máte následující jednoduchý kód XML:  
  
 **Vstup**  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 Vstup je v paměti vyjádřené následující uzel stromu s vlastností typu přiřazené uzlu:  
  
 ![Příklad uzlu stromu](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")  
Knihy a název uzlu stromu reprezentace  
  
 `book` Element stane **XmlElement** objektu, na další prvek `title`, se stane **XmlElement**, když se stane obsahu elementu **XmlText** objektu. V prohlížení **XmlElement** metody a vlastnosti, metody a vlastnosti, které se liší od metody a vlastnosti, které jsou k dispozici na **XmlText** objektu. Znalost tak, jaký typ uzlu se změní na kód XML je důležité, protože jeho typ uzlu určuje akce, které lze provést.  
  
 Následující příklad načte v datech XML a zapíše se jiný text, v závislosti na typu uzlu. Pomocí následujících datového souboru XML jako vstup, **items.xml**:  
  
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
  
 Následující kód například čtení **items.xml** souboru a zobrazí se informace pro každý typ uzlu.  
  
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
  
 **Output**  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 Pořízení vstupní jeden řádek v čase a pomocí výstup generovaný z kódu, můžete k analýze co uzel testovací generované řádky, které výstup, a tím pochopení, jaká data XML se aktivovala jaký druh typu uzlu v následující tabulce.  
  
|Vstup|Výstup|Test typu uzlu|  
|-----------|------------|--------------------|  
|\<? xml verze = "1.0"? >|\<? xml verze = "1.0'? >|XmlNodeType.XmlDeclaration|  
|\<! – Toto je ukázkový dokumentu XML-->|\<! – Toto je ukázkový dokumentu XML-->|XmlNodeType.Comment|  
|\<! Položky DOCTYPE [\<! Počet ENTIT "123" >] >|\<! Položky DOCTYPE [\<! Počet ENTIT "123" >]|XmlNodeType.DocumentType|  
|\<Položky >|\<Položky >|Očekáván element XmlNodeType.Element|  
|\<Položka >|\<Položka >|Očekáván element XmlNodeType.Element|  
|Testování s převodem entity: &number;|Test s entitou: 123|XmlNodeType.Text|  
|\</ Položky >|\</ Položky >|XmlNodeType.EndElement|  
|\<Položka >|\<Položka >|XmNodeType.Element|  
|testování s podřízený element|testování s podřízený element|XmlNodeType.Text|  
|\<Další >|\<Další >|Očekáván element XmlNodeType.Element|  
|vlastní položky|vlastní položky|XmlNodeType.Text|  
|\</ Položky >|\</ Položky >|XmlNodeType.EndElement|  
|\<Položka >|\<Položka >|Očekáván element XmlNodeType.Element|  
|testování s oddílu CDATA|testování s oddílu CDATA|XmlTest.Text|  
|&LT;! [CDATA [\<456 &GT;]]\>|&LT;! [CDATA [\<456 &GT;]]\>|XmlTest.CDATA|  
|DEF|DEF|XmlNodeType.Text|  
|\</ Položky >|\</ Položky >|XmlNodeType.EndElement|  
|\<Položka >|\<Položka >|Očekáván element XmlNodeType.Element|  
|Test se entitou char: &\#65;|Test se entitou char: A|XmlNodeType.Text|  
|\</ Položky >|\</ Položky >|XmlNodeType.EndElement|  
|\<!----> Čtrnáct znaků v tomto elementu.|\<----> Čtrnáct znaků v tomto elementu.|XmlNodeType.Comment|  
|\<Položka >|\<Položka >|Očekáván element XmlNodeType.Element|  
|1234567890ABCD|1234567890ABCD|XmlNodeType.Text|  
|\</ Položky >|\</ Položky >|XmlNodeType.EndElement|  
|\</ Položky >|\</ Položky >|XmlNodeType.EndElement|  
  
 Musíte vědět, jaký typ uzlu je přiřazený, jako uzel typ řídí, jaké druhy akce jsou platné a jaký druh vlastnosti můžete nastavit a načíst.  
  
 Vytvoření uzlu pro mezer je řízena, když je načíst data do modelu DOM pomocí **PreserveWhitespace** příznak. Další informace najdete v tématu [mezer a významné zpracování mezer při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).  
  
 Přidání nových uzlů k modelu DOM naleznete v tématu [vkládání uzly do dokumentu XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md). Odebrat uzly z modelu DOM, najdete v části [odebrání uzlů, obsah a hodnoty z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md). Chcete-li upravit obsah uzly v modelu DOM, přečtěte si téma [úprava uzlů, obsah a hodnoty v dokumentu XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
