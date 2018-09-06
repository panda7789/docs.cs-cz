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
ms.openlocfilehash: b1808121049c6344b72b1c9d99e19c46422dfa0c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042555"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="b56ba-102">Mapování hierarchie objektů na XML Data</span><span class="sxs-lookup"><span data-stu-id="b56ba-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="b56ba-103">Když je dokument XML v paměti, koncepční reprezentace je strom.</span><span class="sxs-lookup"><span data-stu-id="b56ba-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="b56ba-104">Pro programování, můžete mít hierarchii objektů pro přístup k uzly stromu.</span><span class="sxs-lookup"><span data-stu-id="b56ba-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="b56ba-105">Následující příklad ukazuje, jak obsah XML stane uzly.</span><span class="sxs-lookup"><span data-stu-id="b56ba-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="b56ba-106">XML je pro čtení do XML Document Object Model (DOM), kusy jsou přeloženy do uzlů a další metadata o samotné, jako je například jejich typ uzlu a hodnoty uchovávat tyto uzly.</span><span class="sxs-lookup"><span data-stu-id="b56ba-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="b56ba-107">Typ uzlu je její objekt a co určuje, jaké akce lze provádět a které vlastnosti můžete nastavit nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="b56ba-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="b56ba-108">Pokud máte následující jednoduchý kód XML:</span><span class="sxs-lookup"><span data-stu-id="b56ba-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="b56ba-109">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="b56ba-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="b56ba-110">Vstup je vyjádřena v paměti jako následující uzel stromu s vlastností typu přiřazeném uzlu:</span><span class="sxs-lookup"><span data-stu-id="b56ba-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="b56ba-111">![Příklad uzlu stromu](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="b56ba-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="b56ba-112">Knihy a název reprezentace uzlu stromu</span><span class="sxs-lookup"><span data-stu-id="b56ba-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="b56ba-113">`book` Prvek stane **XmlElement** objektu, další prvek `title`, stane **XmlElement**, přestože obsah elementu se stane **XmlText** objektu.</span><span class="sxs-lookup"><span data-stu-id="b56ba-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="b56ba-114">V podíváme **XmlElement** metody a vlastnosti, metody a vlastnosti, které se liší od metody a vlastnosti, které jsou k dispozici na **XmlText** objektu.</span><span class="sxs-lookup"><span data-stu-id="b56ba-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="b56ba-115">Takže vědět, jaký typ uzlu, bude kód XML je důležité, protože jeho typ uzlu určuje akce, které lze provést.</span><span class="sxs-lookup"><span data-stu-id="b56ba-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="b56ba-116">Následující příklad načte v datech XML a zapíše jiný text, v závislosti na typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="b56ba-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="b56ba-117">Pomocí následujících datového souboru XML jako vstup, **items.xml**:</span><span class="sxs-lookup"><span data-stu-id="b56ba-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="b56ba-118">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="b56ba-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="b56ba-119">Následující příklad čte kód **items.xml** soubor a zobrazí informace pro každý typ uzlu.</span><span class="sxs-lookup"><span data-stu-id="b56ba-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="b56ba-120">Výstup z příkladu zobrazí mapování dat na typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="b56ba-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="b56ba-121">**Output**</span><span class="sxs-lookup"><span data-stu-id="b56ba-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 <span data-ttu-id="b56ba-122">Trvá jeden vstup najednou a používání výstup generovaný z kódu, můžete analyzovat, jaké test uzlu vygeneruje výstup, které řádky a vysvětlení, jaká data XML začal být jaký druh typu uzlu v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b56ba-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="b56ba-123">Vstup</span><span class="sxs-lookup"><span data-stu-id="b56ba-123">Input</span></span>|<span data-ttu-id="b56ba-124">Výstup</span><span class="sxs-lookup"><span data-stu-id="b56ba-124">Output</span></span>|<span data-ttu-id="b56ba-125">Test typ uzlu</span><span class="sxs-lookup"><span data-stu-id="b56ba-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="b56ba-126">\<? xml verze = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="b56ba-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="b56ba-127">\<? xml verze = "1.0'? ></span><span class="sxs-lookup"><span data-stu-id="b56ba-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="b56ba-128">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="b56ba-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="b56ba-129">\<! – Toto je ukázkový dokument XML--></span><span class="sxs-lookup"><span data-stu-id="b56ba-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="b56ba-130">\<! – Toto je ukázkový dokument XML--></span><span class="sxs-lookup"><span data-stu-id="b56ba-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="b56ba-131">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="b56ba-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="b56ba-132">\<! Typ dokumentu položky [\<! Počet ENTIT "123" >] ></span><span class="sxs-lookup"><span data-stu-id="b56ba-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="b56ba-133">\<! Typ dokumentu položky [\<! Počet ENTIT "123" >]</span><span class="sxs-lookup"><span data-stu-id="b56ba-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="b56ba-134">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="b56ba-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="b56ba-135">\<Položky ></span><span class="sxs-lookup"><span data-stu-id="b56ba-135">\<Items></span></span>|<span data-ttu-id="b56ba-136">\<Položky ></span><span class="sxs-lookup"><span data-stu-id="b56ba-136">\<Items></span></span>|<span data-ttu-id="b56ba-137">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b56ba-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b56ba-138">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-138">\<Item></span></span>|<span data-ttu-id="b56ba-139">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-139">\<Item></span></span>|<span data-ttu-id="b56ba-140">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b56ba-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b56ba-141">Testování s převodem entity: &number;</span><span class="sxs-lookup"><span data-stu-id="b56ba-141">Test with an entity: &number;</span></span>|<span data-ttu-id="b56ba-142">Test s převodem entity: 123</span><span class="sxs-lookup"><span data-stu-id="b56ba-142">Test with an entity: 123</span></span>|<span data-ttu-id="b56ba-143">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b56ba-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b56ba-144">\</ Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-144">\</Item></span></span>|<span data-ttu-id="b56ba-145">\</ Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-145">\</Item></span></span>|<span data-ttu-id="b56ba-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b56ba-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="b56ba-147">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-147">\<Item></span></span>|<span data-ttu-id="b56ba-148">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-148">\<Item></span></span>|<span data-ttu-id="b56ba-149">XmNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b56ba-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="b56ba-150">testování s podřízeným elementem</span><span class="sxs-lookup"><span data-stu-id="b56ba-150">test with a child element</span></span>|<span data-ttu-id="b56ba-151">testování s podřízeným elementem</span><span class="sxs-lookup"><span data-stu-id="b56ba-151">test with a child element</span></span>|<span data-ttu-id="b56ba-152">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b56ba-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b56ba-153">\<Další ></span><span class="sxs-lookup"><span data-stu-id="b56ba-153">\<more></span></span>|<span data-ttu-id="b56ba-154">\<Další ></span><span class="sxs-lookup"><span data-stu-id="b56ba-154">\<more></span></span>|<span data-ttu-id="b56ba-155">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b56ba-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b56ba-156">věci</span><span class="sxs-lookup"><span data-stu-id="b56ba-156">stuff</span></span>|<span data-ttu-id="b56ba-157">věci</span><span class="sxs-lookup"><span data-stu-id="b56ba-157">stuff</span></span>|<span data-ttu-id="b56ba-158">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b56ba-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b56ba-159">\</ Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-159">\</Item></span></span>|<span data-ttu-id="b56ba-160">\</ Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-160">\</Item></span></span>|<span data-ttu-id="b56ba-161">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b56ba-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="b56ba-162">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-162">\<Item></span></span>|<span data-ttu-id="b56ba-163">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-163">\<Item></span></span>|<span data-ttu-id="b56ba-164">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b56ba-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b56ba-165">testování pomocí sekce CDATA</span><span class="sxs-lookup"><span data-stu-id="b56ba-165">test with a CDATA section</span></span>|<span data-ttu-id="b56ba-166">testování pomocí sekce CDATA</span><span class="sxs-lookup"><span data-stu-id="b56ba-166">test with a CDATA section</span></span>|<span data-ttu-id="b56ba-167">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="b56ba-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="b56ba-168">&LT;! [CDATA [\<456 &GT;]]\></span><span class="sxs-lookup"><span data-stu-id="b56ba-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="b56ba-169">&LT;! [CDATA [\<456 &GT;]]\></span><span class="sxs-lookup"><span data-stu-id="b56ba-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="b56ba-170">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="b56ba-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="b56ba-171">DEF</span><span class="sxs-lookup"><span data-stu-id="b56ba-171">def</span></span>|<span data-ttu-id="b56ba-172">DEF</span><span class="sxs-lookup"><span data-stu-id="b56ba-172">def</span></span>|<span data-ttu-id="b56ba-173">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b56ba-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b56ba-174">\</ Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-174">\</Item></span></span>|<span data-ttu-id="b56ba-175">\</ Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-175">\</Item></span></span>|<span data-ttu-id="b56ba-176">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b56ba-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="b56ba-177">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-177">\<Item></span></span>|<span data-ttu-id="b56ba-178">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-178">\<Item></span></span>|<span data-ttu-id="b56ba-179">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b56ba-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b56ba-180">Test s entitou char: &\#65;</span><span class="sxs-lookup"><span data-stu-id="b56ba-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="b56ba-181">Test s entitou char: A</span><span class="sxs-lookup"><span data-stu-id="b56ba-181">Test with a char entity: A</span></span>|<span data-ttu-id="b56ba-182">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b56ba-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b56ba-183">\</ Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-183">\</Item></span></span>|<span data-ttu-id="b56ba-184">\</ Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-184">\</Item></span></span>|<span data-ttu-id="b56ba-185">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b56ba-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="b56ba-186">\<! –--> Čtrnáct znaky v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="b56ba-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="b56ba-187">\<----> Čtrnáct znaky v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="b56ba-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="b56ba-188">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="b56ba-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="b56ba-189">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-189">\<Item></span></span>|<span data-ttu-id="b56ba-190">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-190">\<Item></span></span>|<span data-ttu-id="b56ba-191">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="b56ba-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="b56ba-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="b56ba-192">1234567890ABCD</span></span>|<span data-ttu-id="b56ba-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="b56ba-193">1234567890ABCD</span></span>|<span data-ttu-id="b56ba-194">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="b56ba-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="b56ba-195">\</ Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-195">\</Item></span></span>|<span data-ttu-id="b56ba-196">\</ Položka ></span><span class="sxs-lookup"><span data-stu-id="b56ba-196">\</Item></span></span>|<span data-ttu-id="b56ba-197">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b56ba-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="b56ba-198">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="b56ba-198">\</Items></span></span>|<span data-ttu-id="b56ba-199">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="b56ba-199">\</Items></span></span>|<span data-ttu-id="b56ba-200">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="b56ba-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="b56ba-201">Musíte vědět, jaký typ uzlu je přiřazen, jako uzel typ řídí, jaké druhy akce jsou platná a jaký druh vlastnosti můžete nastavit a načíst.</span><span class="sxs-lookup"><span data-stu-id="b56ba-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="b56ba-202">Vytvoření uzlu pro prázdné místo je řízena, když data se načtou do modelu DOM pomocí **PreserveWhitespace** příznak.</span><span class="sxs-lookup"><span data-stu-id="b56ba-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="b56ba-203">Další informace najdete v tématu [mezer a významných mezer zpracování při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="b56ba-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="b56ba-204">Přidání nových uzlů v modelu DOM naleznete v tématu [vkládání uzlů do dokumentu XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b56ba-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="b56ba-205">Na odebrání uzlů z modelu DOM, naleznete v tématu [odebrání uzlů, obsahu a hodnot z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b56ba-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="b56ba-206">Pokud chcete upravit obsah uzlů v modelu DOM, naleznete v tématu [úprava uzlů, obsahu a hodnot v dokumentu XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b56ba-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b56ba-207">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b56ba-207">See also</span></span>

- [<span data-ttu-id="b56ba-208">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="b56ba-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
