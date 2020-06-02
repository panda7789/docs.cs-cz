---
title: Mapování hierarchie objektů na data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 8507c4b323f97279c3054b76aaf8d52f14f0d4ad
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289132"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="c60e4-102">Mapování hierarchie objektů na data XML</span><span class="sxs-lookup"><span data-stu-id="c60e4-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="c60e4-103">V případě, že je dokument XML v paměti, konceptuální reprezentace je strom.</span><span class="sxs-lookup"><span data-stu-id="c60e4-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="c60e4-104">Pro programování máte hierarchii objektů pro přístup k uzlům stromu.</span><span class="sxs-lookup"><span data-stu-id="c60e4-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="c60e4-105">Následující příklad ukazuje, jak se obsah XML stávají uzly.</span><span class="sxs-lookup"><span data-stu-id="c60e4-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="c60e4-106">Jelikož je XML čteno do XML model DOM (Document Object Model) (DOM), části jsou přeloženy do uzlů a tyto uzly uchovávají další metadata o sebe, jako je například typ a hodnoty jejich uzlu.</span><span class="sxs-lookup"><span data-stu-id="c60e4-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="c60e4-107">Typ uzlu je jeho objekt a je to, co určuje akce, které lze provést a které vlastnosti lze nastavit nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="c60e4-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="c60e4-108">Pokud máte následující jednoduchý kód XML:</span><span class="sxs-lookup"><span data-stu-id="c60e4-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="c60e4-109">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="c60e4-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="c60e4-110">Vstup je reprezentován v paměti jako následující strom uzlu s přiřazenou vlastností typu uzlu:</span><span class="sxs-lookup"><span data-stu-id="c60e4-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="c60e4-111">![Příklad stromu uzlu](media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="c60e4-111">![example node tree](media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="c60e4-112">Reprezentace stromu uzlů v knize a názvu</span><span class="sxs-lookup"><span data-stu-id="c60e4-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="c60e4-113">`book`Prvek se stala objektem **XmlElement** , další prvek se `title` také stal atributem **XmlElement**, zatímco obsah elementu se stala objektem **XmlText** .</span><span class="sxs-lookup"><span data-stu-id="c60e4-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="c60e4-114">Při prohlížení metod a vlastností třídy **XmlElement** se metody a vlastnosti liší od metod a vlastností dostupných v objektu **XmlText** .</span><span class="sxs-lookup"><span data-stu-id="c60e4-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="c60e4-115">Proto si poznáte, jaký typ uzlu se kód XML stává zásadní, protože jeho typ uzlu určuje akce, které lze provést.</span><span class="sxs-lookup"><span data-stu-id="c60e4-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="c60e4-116">Následující příklad přečte v datech XML a zapisuje jiný text v závislosti na typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="c60e4-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="c60e4-117">Použijte následující datový soubor XML jako Input, **Items. XML**:</span><span class="sxs-lookup"><span data-stu-id="c60e4-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="c60e4-118">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="c60e4-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="c60e4-119">Následující příklad kódu přečte soubor **Items. XML** a zobrazí informace pro každý typ uzlu.</span><span class="sxs-lookup"><span data-stu-id="c60e4-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="c60e4-120">Výstup z příkladu odhalí mapování dat na typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="c60e4-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="c60e4-121">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="c60e4-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>
```  
  
 <span data-ttu-id="c60e4-122">Přebírání jednoho řádku a použití výstupu vygenerovaného z kódu, můžete použít následující tabulku k analýze, který test uzlu vygeneroval, které řádky výstupu, a tím i informace o tom, jaká data XML se staly typem typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="c60e4-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="c60e4-123">Vstup</span><span class="sxs-lookup"><span data-stu-id="c60e4-123">Input</span></span>|<span data-ttu-id="c60e4-124">Výstup</span><span class="sxs-lookup"><span data-stu-id="c60e4-124">Output</span></span>|<span data-ttu-id="c60e4-125">Test typu uzlu</span><span class="sxs-lookup"><span data-stu-id="c60e4-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|\<?xml version="1.0"?>|\<?xml version='1.0'?>|<span data-ttu-id="c60e4-126">XmlNodeType. XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="c60e4-126">XmlNodeType.XmlDeclaration</span></span>|  
|\<!-- This is a sample XML document -->|\<!--This is a sample XML document -->|<span data-ttu-id="c60e4-127">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="c60e4-127">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="c60e4-128">\<!DOCTYPE Items [\<!ENTITY number "123">] ></span><span class="sxs-lookup"><span data-stu-id="c60e4-128">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="c60e4-129">\<!DOCTYPE Items [\<!ENTITY number "123">]</span><span class="sxs-lookup"><span data-stu-id="c60e4-129">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="c60e4-130">XmlNodeType. DocumentType</span><span class="sxs-lookup"><span data-stu-id="c60e4-130">XmlNodeType.DocumentType</span></span>|  
|\<Items>|\<Items>|<span data-ttu-id="c60e4-131">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="c60e4-131">XmlNodeType.Element</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="c60e4-132">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="c60e4-132">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="c60e4-133">Test s entitou:&number;</span><span class="sxs-lookup"><span data-stu-id="c60e4-133">Test with an entity: &number;</span></span>|<span data-ttu-id="c60e4-134">Test s entitou: 123</span><span class="sxs-lookup"><span data-stu-id="c60e4-134">Test with an entity: 123</span></span>|<span data-ttu-id="c60e4-135">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="c60e4-135">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="c60e4-136">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="c60e4-136">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="c60e4-137">XmNodeType. element</span><span class="sxs-lookup"><span data-stu-id="c60e4-137">XmNodeType.Element</span></span>|  
|<span data-ttu-id="c60e4-138">test s podřízeným elementem</span><span class="sxs-lookup"><span data-stu-id="c60e4-138">test with a child element</span></span>|<span data-ttu-id="c60e4-139">test s podřízeným elementem</span><span class="sxs-lookup"><span data-stu-id="c60e4-139">test with a child element</span></span>|<span data-ttu-id="c60e4-140">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="c60e4-140">XmlNodeType.Text</span></span>|  
|\<more>|\<more>|<span data-ttu-id="c60e4-141">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="c60e4-141">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="c60e4-142">vhodné</span><span class="sxs-lookup"><span data-stu-id="c60e4-142">stuff</span></span>|<span data-ttu-id="c60e4-143">vhodné</span><span class="sxs-lookup"><span data-stu-id="c60e4-143">stuff</span></span>|<span data-ttu-id="c60e4-144">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="c60e4-144">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="c60e4-145">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="c60e4-145">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="c60e4-146">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="c60e4-146">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="c60e4-147">testování pomocí oddílu CDATA</span><span class="sxs-lookup"><span data-stu-id="c60e4-147">test with a CDATA section</span></span>|<span data-ttu-id="c60e4-148">testování pomocí oddílu CDATA</span><span class="sxs-lookup"><span data-stu-id="c60e4-148">test with a CDATA section</span></span>|<span data-ttu-id="c60e4-149">XmlTest. text</span><span class="sxs-lookup"><span data-stu-id="c60e4-149">XmlTest.Text</span></span>|  
|<span data-ttu-id="c60e4-150"><! [CDATA [ \<456> ]]\></span><span class="sxs-lookup"><span data-stu-id="c60e4-150"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="c60e4-151"><! [CDATA [ \<456> ]]\></span><span class="sxs-lookup"><span data-stu-id="c60e4-151"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="c60e4-152">XmlTest. CDATA</span><span class="sxs-lookup"><span data-stu-id="c60e4-152">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="c60e4-153">IME</span><span class="sxs-lookup"><span data-stu-id="c60e4-153">def</span></span>|<span data-ttu-id="c60e4-154">IME</span><span class="sxs-lookup"><span data-stu-id="c60e4-154">def</span></span>|<span data-ttu-id="c60e4-155">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="c60e4-155">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="c60e4-156">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="c60e4-156">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="c60e4-157">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="c60e4-157">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="c60e4-158">Test s entitou char: &\# 65;</span><span class="sxs-lookup"><span data-stu-id="c60e4-158">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="c60e4-159">Test s entitou char: A</span><span class="sxs-lookup"><span data-stu-id="c60e4-159">Test with a char entity: A</span></span>|<span data-ttu-id="c60e4-160">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="c60e4-160">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="c60e4-161">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="c60e4-161">XmlNodeType.EndElement</span></span>|  
|\<!-- Fourteen chars in this element.-->|\<--Fourteen chars in this element.-->|<span data-ttu-id="c60e4-162">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="c60e4-162">XmlNodeType.Comment</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="c60e4-163">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="c60e4-163">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="c60e4-164">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="c60e4-164">1234567890ABCD</span></span>|<span data-ttu-id="c60e4-165">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="c60e4-165">1234567890ABCD</span></span>|<span data-ttu-id="c60e4-166">XmlNodeType. text</span><span class="sxs-lookup"><span data-stu-id="c60e4-166">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="c60e4-167">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="c60e4-167">XmlNodeType.EndElement</span></span>|  
|\</Items>|\</Items>|<span data-ttu-id="c60e4-168">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="c60e4-168">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="c60e4-169">Musíte znát typ uzlu, který je přiřazen, protože typ uzlu řídí, jaké druhy akcí jsou platné a jaký druh vlastností lze nastavit a načíst.</span><span class="sxs-lookup"><span data-stu-id="c60e4-169">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="c60e4-170">Vytváření uzlů pro prázdné znaky je řízeno při načtení dat do modelu DOM příznakem **PreserveWhitespace** .</span><span class="sxs-lookup"><span data-stu-id="c60e4-170">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="c60e4-171">Další informace naleznete v tématu [mezera a významná manipulace s prázdným znakem při načítání modelu DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="c60e4-171">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="c60e4-172">Chcete-li přidat nové uzly do modelu DOM, přečtěte si téma [vkládání uzlů do dokumentu XML](inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="c60e4-172">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="c60e4-173">Chcete-li odebrat uzly z modelu DOM, přečtěte si téma [Odebrání uzlů, obsahu a hodnot z dokumentu XML](removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="c60e4-173">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="c60e4-174">Chcete-li upravit obsah uzlů v modelu DOM, přečtěte si téma [Úprava uzlů, obsahu a hodnot v dokumentu XML](modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="c60e4-174">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c60e4-175">Viz také</span><span class="sxs-lookup"><span data-stu-id="c60e4-175">See also</span></span>

- [<span data-ttu-id="c60e4-176">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="c60e4-176">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
