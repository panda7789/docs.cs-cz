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
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="79f24-102">Mapování hierarchie objektů na XML Data</span><span class="sxs-lookup"><span data-stu-id="79f24-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="79f24-103">Když je dokument XML v paměti, je koncepční reprezentace stromu.</span><span class="sxs-lookup"><span data-stu-id="79f24-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="79f24-104">Pro programování, nebudete mít hierarchii k objektu pro přístup k uzlu stromu.</span><span class="sxs-lookup"><span data-stu-id="79f24-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="79f24-105">Následující příklad ukazuje, jak se změní obsah XML na uzly.</span><span class="sxs-lookup"><span data-stu-id="79f24-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="79f24-106">Soubor XML je pro čtení do XML modelu DOM (Document Object), jsou převedeny na požadované do uzlů a tyto uzly ukládat další metadata o sami, například jejich typ uzlu a hodnoty.</span><span class="sxs-lookup"><span data-stu-id="79f24-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="79f24-107">Typ uzlu je jeho objekt a je co určuje, jaké akce lze provést a co vlastnosti nelze nastavit ani načíst.</span><span class="sxs-lookup"><span data-stu-id="79f24-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="79f24-108">Pokud máte následující jednoduchý kód XML:</span><span class="sxs-lookup"><span data-stu-id="79f24-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="79f24-109">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="79f24-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="79f24-110">Vstup je v paměti vyjádřené následující uzel stromu s vlastností typu přiřazené uzlu:</span><span class="sxs-lookup"><span data-stu-id="79f24-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="79f24-111">![Příklad uzlu stromu](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="79f24-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="79f24-112">Knihy a název uzlu stromu reprezentace</span><span class="sxs-lookup"><span data-stu-id="79f24-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="79f24-113">`book` Element stane **XmlElement** objektu, na další prvek `title`, se stane **XmlElement**, když se stane obsahu elementu **XmlText** objektu.</span><span class="sxs-lookup"><span data-stu-id="79f24-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="79f24-114">V prohlížení **XmlElement** metody a vlastnosti, metody a vlastnosti, které se liší od metody a vlastnosti, které jsou k dispozici na **XmlText** objektu.</span><span class="sxs-lookup"><span data-stu-id="79f24-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="79f24-115">Znalost tak, jaký typ uzlu se změní na kód XML je důležité, protože jeho typ uzlu určuje akce, které lze provést.</span><span class="sxs-lookup"><span data-stu-id="79f24-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="79f24-116">Následující příklad načte v datech XML a zapíše se jiný text, v závislosti na typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="79f24-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="79f24-117">Pomocí následujících datového souboru XML jako vstup, **items.xml**:</span><span class="sxs-lookup"><span data-stu-id="79f24-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="79f24-118">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="79f24-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="79f24-119">Následující kód například čtení **items.xml** souboru a zobrazí se informace pro každý typ uzlu.</span><span class="sxs-lookup"><span data-stu-id="79f24-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="79f24-120">Výstup z příkladu odhalí mapování dat na typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="79f24-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="79f24-121">**Output**</span><span class="sxs-lookup"><span data-stu-id="79f24-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 <span data-ttu-id="79f24-122">Pořízení vstupní jeden řádek v čase a pomocí výstup generovaný z kódu, můžete k analýze co uzel testovací generované řádky, které výstup, a tím pochopení, jaká data XML se aktivovala jaký druh typu uzlu v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="79f24-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="79f24-123">Vstup</span><span class="sxs-lookup"><span data-stu-id="79f24-123">Input</span></span>|<span data-ttu-id="79f24-124">Výstup</span><span class="sxs-lookup"><span data-stu-id="79f24-124">Output</span></span>|<span data-ttu-id="79f24-125">Test typu uzlu</span><span class="sxs-lookup"><span data-stu-id="79f24-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="79f24-126">\<? xml verze = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="79f24-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="79f24-127">\<? xml verze = "1.0'? ></span><span class="sxs-lookup"><span data-stu-id="79f24-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="79f24-128">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="79f24-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="79f24-129">\<! – Toto je ukázkový dokumentu XML--></span><span class="sxs-lookup"><span data-stu-id="79f24-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="79f24-130">\<! – Toto je ukázkový dokumentu XML--></span><span class="sxs-lookup"><span data-stu-id="79f24-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="79f24-131">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="79f24-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="79f24-132">\<! Položky DOCTYPE [\<! Počet ENTIT "123" >] ></span><span class="sxs-lookup"><span data-stu-id="79f24-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="79f24-133">\<! Položky DOCTYPE [\<! Počet ENTIT "123" >]</span><span class="sxs-lookup"><span data-stu-id="79f24-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="79f24-134">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="79f24-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="79f24-135">\<Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-135">\<Items></span></span>|<span data-ttu-id="79f24-136">\<Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-136">\<Items></span></span>|<span data-ttu-id="79f24-137">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="79f24-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="79f24-138">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="79f24-138">\<Item></span></span>|<span data-ttu-id="79f24-139">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="79f24-139">\<Item></span></span>|<span data-ttu-id="79f24-140">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="79f24-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="79f24-141">Testování s převodem entity: &number;</span><span class="sxs-lookup"><span data-stu-id="79f24-141">Test with an entity: &number;</span></span>|<span data-ttu-id="79f24-142">Test s entitou: 123</span><span class="sxs-lookup"><span data-stu-id="79f24-142">Test with an entity: 123</span></span>|<span data-ttu-id="79f24-143">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="79f24-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="79f24-144">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-144">\</Item></span></span>|<span data-ttu-id="79f24-145">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-145">\</Item></span></span>|<span data-ttu-id="79f24-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="79f24-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="79f24-147">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="79f24-147">\<Item></span></span>|<span data-ttu-id="79f24-148">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="79f24-148">\<Item></span></span>|<span data-ttu-id="79f24-149">XmNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="79f24-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="79f24-150">testování s podřízený element</span><span class="sxs-lookup"><span data-stu-id="79f24-150">test with a child element</span></span>|<span data-ttu-id="79f24-151">testování s podřízený element</span><span class="sxs-lookup"><span data-stu-id="79f24-151">test with a child element</span></span>|<span data-ttu-id="79f24-152">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="79f24-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="79f24-153">\<Další ></span><span class="sxs-lookup"><span data-stu-id="79f24-153">\<more></span></span>|<span data-ttu-id="79f24-154">\<Další ></span><span class="sxs-lookup"><span data-stu-id="79f24-154">\<more></span></span>|<span data-ttu-id="79f24-155">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="79f24-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="79f24-156">vlastní položky</span><span class="sxs-lookup"><span data-stu-id="79f24-156">stuff</span></span>|<span data-ttu-id="79f24-157">vlastní položky</span><span class="sxs-lookup"><span data-stu-id="79f24-157">stuff</span></span>|<span data-ttu-id="79f24-158">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="79f24-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="79f24-159">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-159">\</Item></span></span>|<span data-ttu-id="79f24-160">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-160">\</Item></span></span>|<span data-ttu-id="79f24-161">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="79f24-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="79f24-162">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="79f24-162">\<Item></span></span>|<span data-ttu-id="79f24-163">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="79f24-163">\<Item></span></span>|<span data-ttu-id="79f24-164">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="79f24-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="79f24-165">testování s oddílu CDATA</span><span class="sxs-lookup"><span data-stu-id="79f24-165">test with a CDATA section</span></span>|<span data-ttu-id="79f24-166">testování s oddílu CDATA</span><span class="sxs-lookup"><span data-stu-id="79f24-166">test with a CDATA section</span></span>|<span data-ttu-id="79f24-167">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="79f24-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="79f24-168">&LT;! [CDATA [\<456 &GT;]]\></span><span class="sxs-lookup"><span data-stu-id="79f24-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="79f24-169">&LT;! [CDATA [\<456 &GT;]]\></span><span class="sxs-lookup"><span data-stu-id="79f24-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="79f24-170">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="79f24-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="79f24-171">DEF</span><span class="sxs-lookup"><span data-stu-id="79f24-171">def</span></span>|<span data-ttu-id="79f24-172">DEF</span><span class="sxs-lookup"><span data-stu-id="79f24-172">def</span></span>|<span data-ttu-id="79f24-173">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="79f24-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="79f24-174">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-174">\</Item></span></span>|<span data-ttu-id="79f24-175">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-175">\</Item></span></span>|<span data-ttu-id="79f24-176">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="79f24-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="79f24-177">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="79f24-177">\<Item></span></span>|<span data-ttu-id="79f24-178">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="79f24-178">\<Item></span></span>|<span data-ttu-id="79f24-179">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="79f24-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="79f24-180">Test se entitou char: &\#65;</span><span class="sxs-lookup"><span data-stu-id="79f24-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="79f24-181">Test se entitou char: A</span><span class="sxs-lookup"><span data-stu-id="79f24-181">Test with a char entity: A</span></span>|<span data-ttu-id="79f24-182">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="79f24-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="79f24-183">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-183">\</Item></span></span>|<span data-ttu-id="79f24-184">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-184">\</Item></span></span>|<span data-ttu-id="79f24-185">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="79f24-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="79f24-186">\<!----> Čtrnáct znaků v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="79f24-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="79f24-187">\<----> Čtrnáct znaků v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="79f24-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="79f24-188">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="79f24-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="79f24-189">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="79f24-189">\<Item></span></span>|<span data-ttu-id="79f24-190">\<Položka ></span><span class="sxs-lookup"><span data-stu-id="79f24-190">\<Item></span></span>|<span data-ttu-id="79f24-191">Očekáván element XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="79f24-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="79f24-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="79f24-192">1234567890ABCD</span></span>|<span data-ttu-id="79f24-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="79f24-193">1234567890ABCD</span></span>|<span data-ttu-id="79f24-194">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="79f24-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="79f24-195">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-195">\</Item></span></span>|<span data-ttu-id="79f24-196">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-196">\</Item></span></span>|<span data-ttu-id="79f24-197">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="79f24-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="79f24-198">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-198">\</Items></span></span>|<span data-ttu-id="79f24-199">\</ Položky ></span><span class="sxs-lookup"><span data-stu-id="79f24-199">\</Items></span></span>|<span data-ttu-id="79f24-200">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="79f24-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="79f24-201">Musíte vědět, jaký typ uzlu je přiřazený, jako uzel typ řídí, jaké druhy akce jsou platné a jaký druh vlastnosti můžete nastavit a načíst.</span><span class="sxs-lookup"><span data-stu-id="79f24-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="79f24-202">Vytvoření uzlu pro mezer je řízena, když je načíst data do modelu DOM pomocí **PreserveWhitespace** příznak.</span><span class="sxs-lookup"><span data-stu-id="79f24-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="79f24-203">Další informace najdete v tématu [mezer a významné zpracování mezer při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="79f24-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="79f24-204">Přidání nových uzlů k modelu DOM naleznete v tématu [vkládání uzly do dokumentu XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="79f24-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="79f24-205">Odebrat uzly z modelu DOM, najdete v části [odebrání uzlů, obsah a hodnoty z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="79f24-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="79f24-206">Chcete-li upravit obsah uzly v modelu DOM, přečtěte si téma [úprava uzlů, obsah a hodnoty v dokumentu XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="79f24-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f24-207">Viz také</span><span class="sxs-lookup"><span data-stu-id="79f24-207">See Also</span></span>  
 [<span data-ttu-id="79f24-208">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="79f24-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
