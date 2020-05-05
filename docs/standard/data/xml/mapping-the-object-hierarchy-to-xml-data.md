---
title: Mapování hierarchie objektů na data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 4ad505749625e22a09406549329179990b81c140
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794387"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="ce385-102">Mapování hierarchie objektů na data XML</span><span class="sxs-lookup"><span data-stu-id="ce385-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="ce385-103">V případě, že je dokument XML v paměti, konceptuální reprezentace je strom.</span><span class="sxs-lookup"><span data-stu-id="ce385-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="ce385-104">Pro programování máte hierarchii objektů pro přístup k uzlům stromu.</span><span class="sxs-lookup"><span data-stu-id="ce385-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="ce385-105">Následující příklad ukazuje, jak se obsah XML stávají uzly.</span><span class="sxs-lookup"><span data-stu-id="ce385-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="ce385-106">Jelikož je XML čteno do XML model DOM (Document Object Model) (DOM), části jsou přeloženy do uzlů a tyto uzly uchovávají další metadata o sebe, jako je například typ a hodnoty jejich uzlu.</span><span class="sxs-lookup"><span data-stu-id="ce385-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="ce385-107">Typ uzlu je jeho objekt a je to, co určuje akce, které lze provést a které vlastnosti lze nastavit nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="ce385-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="ce385-108">Pokud máte následující jednoduchý kód XML:</span><span class="sxs-lookup"><span data-stu-id="ce385-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="ce385-109">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="ce385-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="ce385-110">Vstup je reprezentován v paměti jako následující strom uzlu s přiřazenou vlastností typu uzlu:</span><span class="sxs-lookup"><span data-stu-id="ce385-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="ce385-111">![Příklad stromu uzlu](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="ce385-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="ce385-112">Reprezentace stromu uzlů v knize a názvu</span><span class="sxs-lookup"><span data-stu-id="ce385-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="ce385-113">`book` Prvek se stala objektem **XmlElement** , další prvek `title`se také stal atributem **XmlElement**, zatímco obsah elementu se stala objektem **XmlText** .</span><span class="sxs-lookup"><span data-stu-id="ce385-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="ce385-114">Při prohlížení metod a vlastností třídy **XmlElement** se metody a vlastnosti liší od metod a vlastností dostupných v objektu **XmlText** .</span><span class="sxs-lookup"><span data-stu-id="ce385-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="ce385-115">Proto si poznáte, jaký typ uzlu se kód XML stává zásadní, protože jeho typ uzlu určuje akce, které lze provést.</span><span class="sxs-lookup"><span data-stu-id="ce385-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="ce385-116">Následující příklad přečte v datech XML a zapisuje jiný text v závislosti na typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="ce385-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="ce385-117">Použijte následující datový soubor XML jako Input, **Items. XML**:</span><span class="sxs-lookup"><span data-stu-id="ce385-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="ce385-118">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="ce385-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="ce385-119">Následující příklad kódu přečte soubor **Items. XML** a zobrazí informace pro každý typ uzlu.</span><span class="sxs-lookup"><span data-stu-id="ce385-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="ce385-120">Výstup z příkladu odhalí mapování dat na typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="ce385-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="ce385-121">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="ce385-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>
```  
  
 <span data-ttu-id="ce385-122">Přebírání jednoho řádku a použití výstupu vygenerovaného z kódu, můžete použít následující tabulku k analýze, který test uzlu vygeneroval, které řádky výstupu, a tím i informace o tom, jaká data XML se staly typem typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="ce385-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="ce385-123">Vstup</span><span class="sxs-lookup"><span data-stu-id="ce385-123">Input</span></span>|<span data-ttu-id="ce385-124">Výstup</span><span class="sxs-lookup"><span data-stu-id="ce385-124">Output</span></span>|<span data-ttu-id="ce385-125">Test typu uzlu</span><span class="sxs-lookup"><span data-stu-id="ce385-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="ce385-126">\<? XML Version = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="ce385-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="ce385-127">\<? XML verze = ' 1.0 '? ></span><span class="sxs-lookup"><span data-stu-id="ce385-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="ce385-128">XmlNodeType. XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="ce385-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="ce385-129">\<!--Toto je ukázkový dokument XML--></span><span class="sxs-lookup"><span data-stu-id="ce385-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="ce385-130">\<!--Toto je ukázkový dokument XML--></span><span class="sxs-lookup"><span data-stu-id="ce385-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="ce385-131">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="ce385-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="ce385-132">\<! Položky DOCTYPE [\<! Číslo ENTITY "123" >] ></span><span class="sxs-lookup"><span data-stu-id="ce385-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="ce385-133">\<! Položky DOCTYPE [\<! Číslo ENTITY "123" >]</span><span class="sxs-lookup"><span data-stu-id="ce385-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="ce385-134">XmlNodeType. DocumentType</span><span class="sxs-lookup"><span data-stu-id="ce385-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="ce385-135">\<> položek</span><span class="sxs-lookup"><span data-stu-id="ce385-135">\<Items></span></span>|<span data-ttu-id="ce385-136">\<> položek</span><span class="sxs-lookup"><span data-stu-id="ce385-136">\<Items></span></span>|<span data-ttu-id="ce385-137">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="ce385-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="ce385-138">\<> položky</span><span class="sxs-lookup"><span data-stu-id="ce385-138">\<Item></span></span>|<span data-ttu-id="ce385-139">\<> položky</span><span class="sxs-lookup"><span data-stu-id="ce385-139">\<Item></span></span>|<span data-ttu-id="ce385-140">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="ce385-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="ce385-141">Test s entitou:&number;</span><span class="sxs-lookup"><span data-stu-id="ce385-141">Test with an entity: &number;</span></span>|<span data-ttu-id="ce385-142">Test s entitou: 123</span><span class="sxs-lookup"><span data-stu-id="ce385-142">Test with an entity: 123</span></span>|<span data-ttu-id="ce385-143">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="ce385-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="ce385-144">\</Item></span><span class="sxs-lookup"><span data-stu-id="ce385-144">\</Item></span></span>|<span data-ttu-id="ce385-145">\</Item></span><span class="sxs-lookup"><span data-stu-id="ce385-145">\</Item></span></span>|<span data-ttu-id="ce385-146">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="ce385-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="ce385-147">\<> položky</span><span class="sxs-lookup"><span data-stu-id="ce385-147">\<Item></span></span>|<span data-ttu-id="ce385-148">\<> položky</span><span class="sxs-lookup"><span data-stu-id="ce385-148">\<Item></span></span>|<span data-ttu-id="ce385-149">XmNodeType. element</span><span class="sxs-lookup"><span data-stu-id="ce385-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="ce385-150">test s podřízeným elementem</span><span class="sxs-lookup"><span data-stu-id="ce385-150">test with a child element</span></span>|<span data-ttu-id="ce385-151">test s podřízeným elementem</span><span class="sxs-lookup"><span data-stu-id="ce385-151">test with a child element</span></span>|<span data-ttu-id="ce385-152">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="ce385-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="ce385-153">\<Další></span><span class="sxs-lookup"><span data-stu-id="ce385-153">\<more></span></span>|<span data-ttu-id="ce385-154">\<Další></span><span class="sxs-lookup"><span data-stu-id="ce385-154">\<more></span></span>|<span data-ttu-id="ce385-155">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="ce385-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="ce385-156">vhodné</span><span class="sxs-lookup"><span data-stu-id="ce385-156">stuff</span></span>|<span data-ttu-id="ce385-157">vhodné</span><span class="sxs-lookup"><span data-stu-id="ce385-157">stuff</span></span>|<span data-ttu-id="ce385-158">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="ce385-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="ce385-159">\</Item></span><span class="sxs-lookup"><span data-stu-id="ce385-159">\</Item></span></span>|<span data-ttu-id="ce385-160">\</Item></span><span class="sxs-lookup"><span data-stu-id="ce385-160">\</Item></span></span>|<span data-ttu-id="ce385-161">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="ce385-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="ce385-162">\<> položky</span><span class="sxs-lookup"><span data-stu-id="ce385-162">\<Item></span></span>|<span data-ttu-id="ce385-163">\<> položky</span><span class="sxs-lookup"><span data-stu-id="ce385-163">\<Item></span></span>|<span data-ttu-id="ce385-164">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="ce385-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="ce385-165">testování pomocí oddílu CDATA</span><span class="sxs-lookup"><span data-stu-id="ce385-165">test with a CDATA section</span></span>|<span data-ttu-id="ce385-166">testování pomocí oddílu CDATA</span><span class="sxs-lookup"><span data-stu-id="ce385-166">test with a CDATA section</span></span>|<span data-ttu-id="ce385-167">XmlTest. text</span><span class="sxs-lookup"><span data-stu-id="ce385-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="ce385-168"><! [CDATA [\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="ce385-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="ce385-169"><! [CDATA [\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="ce385-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="ce385-170">XmlTest. CDATA</span><span class="sxs-lookup"><span data-stu-id="ce385-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="ce385-171">IME</span><span class="sxs-lookup"><span data-stu-id="ce385-171">def</span></span>|<span data-ttu-id="ce385-172">IME</span><span class="sxs-lookup"><span data-stu-id="ce385-172">def</span></span>|<span data-ttu-id="ce385-173">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="ce385-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="ce385-174">\</Item></span><span class="sxs-lookup"><span data-stu-id="ce385-174">\</Item></span></span>|<span data-ttu-id="ce385-175">\</Item></span><span class="sxs-lookup"><span data-stu-id="ce385-175">\</Item></span></span>|<span data-ttu-id="ce385-176">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="ce385-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="ce385-177">\<> položky</span><span class="sxs-lookup"><span data-stu-id="ce385-177">\<Item></span></span>|<span data-ttu-id="ce385-178">\<> položky</span><span class="sxs-lookup"><span data-stu-id="ce385-178">\<Item></span></span>|<span data-ttu-id="ce385-179">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="ce385-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="ce385-180">Test s entitou char: &\#65;</span><span class="sxs-lookup"><span data-stu-id="ce385-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="ce385-181">Test s entitou char: A</span><span class="sxs-lookup"><span data-stu-id="ce385-181">Test with a char entity: A</span></span>|<span data-ttu-id="ce385-182">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="ce385-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="ce385-183">\</Item></span><span class="sxs-lookup"><span data-stu-id="ce385-183">\</Item></span></span>|<span data-ttu-id="ce385-184">\</Item></span><span class="sxs-lookup"><span data-stu-id="ce385-184">\</Item></span></span>|<span data-ttu-id="ce385-185">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="ce385-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="ce385-186">\<V tomto elementu!--čtrnáct znaků.--></span><span class="sxs-lookup"><span data-stu-id="ce385-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="ce385-187">\<--Čtrnáct znaků v tomto elementu.--></span><span class="sxs-lookup"><span data-stu-id="ce385-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="ce385-188">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="ce385-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="ce385-189">\<> položky</span><span class="sxs-lookup"><span data-stu-id="ce385-189">\<Item></span></span>|<span data-ttu-id="ce385-190">\<> položky</span><span class="sxs-lookup"><span data-stu-id="ce385-190">\<Item></span></span>|<span data-ttu-id="ce385-191">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="ce385-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="ce385-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="ce385-192">1234567890ABCD</span></span>|<span data-ttu-id="ce385-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="ce385-193">1234567890ABCD</span></span>|<span data-ttu-id="ce385-194">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="ce385-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="ce385-195">\</Item></span><span class="sxs-lookup"><span data-stu-id="ce385-195">\</Item></span></span>|<span data-ttu-id="ce385-196">\</Item></span><span class="sxs-lookup"><span data-stu-id="ce385-196">\</Item></span></span>|<span data-ttu-id="ce385-197">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="ce385-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="ce385-198">\</Items></span><span class="sxs-lookup"><span data-stu-id="ce385-198">\</Items></span></span>|<span data-ttu-id="ce385-199">\</Items></span><span class="sxs-lookup"><span data-stu-id="ce385-199">\</Items></span></span>|<span data-ttu-id="ce385-200">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="ce385-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="ce385-201">Musíte znát typ uzlu, který je přiřazen, protože typ uzlu řídí, jaké druhy akcí jsou platné a jaký druh vlastností lze nastavit a načíst.</span><span class="sxs-lookup"><span data-stu-id="ce385-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="ce385-202">Vytváření uzlů pro prázdné znaky je řízeno při načtení dat do modelu DOM příznakem **PreserveWhitespace** .</span><span class="sxs-lookup"><span data-stu-id="ce385-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="ce385-203">Další informace naleznete v tématu [mezera a významná manipulace s prázdným znakem při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="ce385-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="ce385-204">Chcete-li přidat nové uzly do modelu DOM, přečtěte si téma [vkládání uzlů do dokumentu XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ce385-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="ce385-205">Chcete-li odebrat uzly z modelu DOM, přečtěte si téma [Odebrání uzlů, obsahu a hodnot z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ce385-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="ce385-206">Chcete-li upravit obsah uzlů v modelu DOM, přečtěte si téma [Úprava uzlů, obsahu a hodnot v dokumentu XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ce385-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce385-207">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce385-207">See also</span></span>

- [<span data-ttu-id="ce385-208">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ce385-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
