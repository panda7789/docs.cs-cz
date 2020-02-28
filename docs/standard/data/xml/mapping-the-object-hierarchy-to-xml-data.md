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
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="134bb-102">Mapování hierarchie objektů na data XML</span><span class="sxs-lookup"><span data-stu-id="134bb-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="134bb-103">V případě, že je dokument XML v paměti, konceptuální reprezentace je strom.</span><span class="sxs-lookup"><span data-stu-id="134bb-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="134bb-104">Pro programování máte hierarchii objektů pro přístup k uzlům stromu.</span><span class="sxs-lookup"><span data-stu-id="134bb-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="134bb-105">Následující příklad ukazuje, jak se obsah XML stávají uzly.</span><span class="sxs-lookup"><span data-stu-id="134bb-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="134bb-106">Jelikož je XML čteno do XML model DOM (Document Object Model) (DOM), části jsou přeloženy do uzlů a tyto uzly uchovávají další metadata o sebe, jako je například typ a hodnoty jejich uzlu.</span><span class="sxs-lookup"><span data-stu-id="134bb-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="134bb-107">Typ uzlu je jeho objekt a je to, co určuje akce, které lze provést a které vlastnosti lze nastavit nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="134bb-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="134bb-108">Pokud máte následující jednoduchý kód XML:</span><span class="sxs-lookup"><span data-stu-id="134bb-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="134bb-109">**Input** (Vstup)</span><span class="sxs-lookup"><span data-stu-id="134bb-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="134bb-110">Vstup je reprezentován v paměti jako následující strom uzlu s přiřazenou vlastností typu uzlu:</span><span class="sxs-lookup"><span data-stu-id="134bb-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="134bb-111">![Příklad stromu uzlu](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="134bb-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="134bb-112">Reprezentace stromu uzlů v knize a názvu</span><span class="sxs-lookup"><span data-stu-id="134bb-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="134bb-113">Element `book` se stal objektem **XmlElement** , další prvek, `title`, se také stal atributem **XmlElement**, zatímco obsah elementu se stala objektem **XmlText** .</span><span class="sxs-lookup"><span data-stu-id="134bb-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="134bb-114">Při prohlížení metod a vlastností třídy **XmlElement** se metody a vlastnosti liší od metod a vlastností dostupných v objektu **XmlText** .</span><span class="sxs-lookup"><span data-stu-id="134bb-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="134bb-115">Proto si poznáte, jaký typ uzlu se kód XML stává zásadní, protože jeho typ uzlu určuje akce, které lze provést.</span><span class="sxs-lookup"><span data-stu-id="134bb-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="134bb-116">Následující příklad přečte v datech XML a zapisuje jiný text v závislosti na typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="134bb-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="134bb-117">Použijte následující datový soubor XML jako Input, **Items. XML**:</span><span class="sxs-lookup"><span data-stu-id="134bb-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="134bb-118">**Input** (Vstup)</span><span class="sxs-lookup"><span data-stu-id="134bb-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="134bb-119">Následující příklad kódu přečte soubor **Items. XML** a zobrazí informace pro každý typ uzlu.</span><span class="sxs-lookup"><span data-stu-id="134bb-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="134bb-120">Výstup z příkladu odhalí mapování dat na typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="134bb-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="134bb-121">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="134bb-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 <span data-ttu-id="134bb-122">Přebírání jednoho řádku a použití výstupu vygenerovaného z kódu, můžete použít následující tabulku k analýze, který test uzlu vygeneroval, které řádky výstupu, a tím i informace o tom, jaká data XML se staly typem typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="134bb-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="134bb-123">Vstup</span><span class="sxs-lookup"><span data-stu-id="134bb-123">Input</span></span>|<span data-ttu-id="134bb-124">Výstup</span><span class="sxs-lookup"><span data-stu-id="134bb-124">Output</span></span>|<span data-ttu-id="134bb-125">Test typu uzlu</span><span class="sxs-lookup"><span data-stu-id="134bb-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="134bb-126">\<? XML verze = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="134bb-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="134bb-127">\<? XML verze = ' 1.0 '? ></span><span class="sxs-lookup"><span data-stu-id="134bb-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="134bb-128">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="134bb-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="134bb-129">\<!--Toto je ukázkový dokument XML – ></span><span class="sxs-lookup"><span data-stu-id="134bb-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="134bb-130">\<!--Toto je ukázkový dokument XML – ></span><span class="sxs-lookup"><span data-stu-id="134bb-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="134bb-131">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="134bb-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="134bb-132">\<! Položky DOCTYPE [\<! Číslo ENTITY "123" >] ></span><span class="sxs-lookup"><span data-stu-id="134bb-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="134bb-133">\<! Položky DOCTYPE [\<! Číslo ENTITY "123" >]</span><span class="sxs-lookup"><span data-stu-id="134bb-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="134bb-134">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="134bb-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="134bb-135">\<položky ></span><span class="sxs-lookup"><span data-stu-id="134bb-135">\<Items></span></span>|<span data-ttu-id="134bb-136">\<položky ></span><span class="sxs-lookup"><span data-stu-id="134bb-136">\<Items></span></span>|<span data-ttu-id="134bb-137">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="134bb-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="134bb-138">Položka \<></span><span class="sxs-lookup"><span data-stu-id="134bb-138">\<Item></span></span>|<span data-ttu-id="134bb-139">Položka \<></span><span class="sxs-lookup"><span data-stu-id="134bb-139">\<Item></span></span>|<span data-ttu-id="134bb-140">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="134bb-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="134bb-141">Test s entitou: &number;</span><span class="sxs-lookup"><span data-stu-id="134bb-141">Test with an entity: &number;</span></span>|<span data-ttu-id="134bb-142">Test s entitou: 123</span><span class="sxs-lookup"><span data-stu-id="134bb-142">Test with an entity: 123</span></span>|<span data-ttu-id="134bb-143">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="134bb-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="134bb-144">\</Item ></span><span class="sxs-lookup"><span data-stu-id="134bb-144">\</Item></span></span>|<span data-ttu-id="134bb-145">\</Item ></span><span class="sxs-lookup"><span data-stu-id="134bb-145">\</Item></span></span>|<span data-ttu-id="134bb-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="134bb-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="134bb-147">Položka \<></span><span class="sxs-lookup"><span data-stu-id="134bb-147">\<Item></span></span>|<span data-ttu-id="134bb-148">Položka \<></span><span class="sxs-lookup"><span data-stu-id="134bb-148">\<Item></span></span>|<span data-ttu-id="134bb-149">XmNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="134bb-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="134bb-150">test s podřízeným elementem</span><span class="sxs-lookup"><span data-stu-id="134bb-150">test with a child element</span></span>|<span data-ttu-id="134bb-151">test s podřízeným elementem</span><span class="sxs-lookup"><span data-stu-id="134bb-151">test with a child element</span></span>|<span data-ttu-id="134bb-152">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="134bb-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="134bb-153">\<Další ></span><span class="sxs-lookup"><span data-stu-id="134bb-153">\<more></span></span>|<span data-ttu-id="134bb-154">\<Další ></span><span class="sxs-lookup"><span data-stu-id="134bb-154">\<more></span></span>|<span data-ttu-id="134bb-155">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="134bb-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="134bb-156">vhodné</span><span class="sxs-lookup"><span data-stu-id="134bb-156">stuff</span></span>|<span data-ttu-id="134bb-157">vhodné</span><span class="sxs-lookup"><span data-stu-id="134bb-157">stuff</span></span>|<span data-ttu-id="134bb-158">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="134bb-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="134bb-159">\</Item ></span><span class="sxs-lookup"><span data-stu-id="134bb-159">\</Item></span></span>|<span data-ttu-id="134bb-160">\</Item ></span><span class="sxs-lookup"><span data-stu-id="134bb-160">\</Item></span></span>|<span data-ttu-id="134bb-161">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="134bb-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="134bb-162">Položka \<></span><span class="sxs-lookup"><span data-stu-id="134bb-162">\<Item></span></span>|<span data-ttu-id="134bb-163">Položka \<></span><span class="sxs-lookup"><span data-stu-id="134bb-163">\<Item></span></span>|<span data-ttu-id="134bb-164">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="134bb-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="134bb-165">testování pomocí oddílu CDATA</span><span class="sxs-lookup"><span data-stu-id="134bb-165">test with a CDATA section</span></span>|<span data-ttu-id="134bb-166">testování pomocí oddílu CDATA</span><span class="sxs-lookup"><span data-stu-id="134bb-166">test with a CDATA section</span></span>|<span data-ttu-id="134bb-167">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="134bb-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="134bb-168"><! [CDATA [\<456 >]]\></span><span class="sxs-lookup"><span data-stu-id="134bb-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="134bb-169"><! [CDATA [\<456 >]]\></span><span class="sxs-lookup"><span data-stu-id="134bb-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="134bb-170">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="134bb-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="134bb-171">IME</span><span class="sxs-lookup"><span data-stu-id="134bb-171">def</span></span>|<span data-ttu-id="134bb-172">IME</span><span class="sxs-lookup"><span data-stu-id="134bb-172">def</span></span>|<span data-ttu-id="134bb-173">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="134bb-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="134bb-174">\</Item ></span><span class="sxs-lookup"><span data-stu-id="134bb-174">\</Item></span></span>|<span data-ttu-id="134bb-175">\</Item ></span><span class="sxs-lookup"><span data-stu-id="134bb-175">\</Item></span></span>|<span data-ttu-id="134bb-176">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="134bb-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="134bb-177">Položka \<></span><span class="sxs-lookup"><span data-stu-id="134bb-177">\<Item></span></span>|<span data-ttu-id="134bb-178">Položka \<></span><span class="sxs-lookup"><span data-stu-id="134bb-178">\<Item></span></span>|<span data-ttu-id="134bb-179">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="134bb-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="134bb-180">Test s entitou char: &\#65;</span><span class="sxs-lookup"><span data-stu-id="134bb-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="134bb-181">Test s entitou char: A</span><span class="sxs-lookup"><span data-stu-id="134bb-181">Test with a char entity: A</span></span>|<span data-ttu-id="134bb-182">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="134bb-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="134bb-183">\</Item ></span><span class="sxs-lookup"><span data-stu-id="134bb-183">\</Item></span></span>|<span data-ttu-id="134bb-184">\</Item ></span><span class="sxs-lookup"><span data-stu-id="134bb-184">\</Item></span></span>|<span data-ttu-id="134bb-185">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="134bb-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="134bb-186">v tomto elementu \<!--čtrnáct znaků.--></span><span class="sxs-lookup"><span data-stu-id="134bb-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="134bb-187">\<– čtrnáct znaků v tomto elementu.--></span><span class="sxs-lookup"><span data-stu-id="134bb-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="134bb-188">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="134bb-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="134bb-189">Položka \<></span><span class="sxs-lookup"><span data-stu-id="134bb-189">\<Item></span></span>|<span data-ttu-id="134bb-190">Položka \<></span><span class="sxs-lookup"><span data-stu-id="134bb-190">\<Item></span></span>|<span data-ttu-id="134bb-191">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="134bb-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="134bb-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="134bb-192">1234567890ABCD</span></span>|<span data-ttu-id="134bb-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="134bb-193">1234567890ABCD</span></span>|<span data-ttu-id="134bb-194">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="134bb-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="134bb-195">\</Item ></span><span class="sxs-lookup"><span data-stu-id="134bb-195">\</Item></span></span>|<span data-ttu-id="134bb-196">\</Item ></span><span class="sxs-lookup"><span data-stu-id="134bb-196">\</Item></span></span>|<span data-ttu-id="134bb-197">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="134bb-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="134bb-198">\</Items ></span><span class="sxs-lookup"><span data-stu-id="134bb-198">\</Items></span></span>|<span data-ttu-id="134bb-199">\</Items ></span><span class="sxs-lookup"><span data-stu-id="134bb-199">\</Items></span></span>|<span data-ttu-id="134bb-200">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="134bb-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="134bb-201">Musíte znát typ uzlu, který je přiřazen, protože typ uzlu řídí, jaké druhy akcí jsou platné a jaký druh vlastností lze nastavit a načíst.</span><span class="sxs-lookup"><span data-stu-id="134bb-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="134bb-202">Vytváření uzlů pro prázdné znaky je řízeno při načtení dat do modelu DOM příznakem **PreserveWhitespace** .</span><span class="sxs-lookup"><span data-stu-id="134bb-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="134bb-203">Další informace naleznete v tématu [mezera a významná manipulace s prázdným znakem při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="134bb-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="134bb-204">Chcete-li přidat nové uzly do modelu DOM, přečtěte si téma [vkládání uzlů do dokumentu XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="134bb-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="134bb-205">Chcete-li odebrat uzly z modelu DOM, přečtěte si téma [Odebrání uzlů, obsahu a hodnot z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="134bb-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="134bb-206">Chcete-li upravit obsah uzlů v modelu DOM, přečtěte si téma [Úprava uzlů, obsahu a hodnot v dokumentu XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="134bb-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="134bb-207">Viz také</span><span class="sxs-lookup"><span data-stu-id="134bb-207">See also</span></span>

- [<span data-ttu-id="134bb-208">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="134bb-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
