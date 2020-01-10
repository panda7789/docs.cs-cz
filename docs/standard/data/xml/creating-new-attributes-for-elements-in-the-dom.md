---
title: Vytváření nových atributů pro elementy v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
ms.openlocfilehash: 79a3390933256ed862d35c90db0aab2177cdfc41
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711009"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="94626-102">Vytváření nových atributů pro elementy v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="94626-102">Creating New Attributes for Elements in the DOM</span></span>

<span data-ttu-id="94626-103">Vytváření nových atributů se liší od vytvoření jiných typů uzlů, protože atributy nejsou uzly, ale jsou vlastnosti uzlu elementu a jsou obsaženy v objektu **XmlAttributeCollection** přidruženého k elementu.</span><span class="sxs-lookup"><span data-stu-id="94626-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="94626-104">Existuje několik způsobů, jak vytvořit atribut a připojit jej k elementu:</span><span class="sxs-lookup"><span data-stu-id="94626-104">There are multiple ways to create an attribute and attach it to an element:</span></span>

- <span data-ttu-id="94626-105">Získejte uzel element a použijte atribut **SetAttributes** pro přidání atributu do kolekce atributů daného elementu.</span><span class="sxs-lookup"><span data-stu-id="94626-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>

- <span data-ttu-id="94626-106">Vytvořte uzel **XmlAttribute** pomocí metody **CreateAttribute** , Získejte uzel element a pak použijte **SetAttributeNode** pro přidání uzlu do kolekce atributů daného elementu.</span><span class="sxs-lookup"><span data-stu-id="94626-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>

<span data-ttu-id="94626-107">Následující příklad ukazuje, jak přidat atribut k elementu pomocí metody **SetAttributes** :</span><span class="sxs-lookup"><span data-stu-id="94626-107">The following example shows how to add an attribute to an element using the **SetAttribute** method:</span></span>

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As New XmlDocument()
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _
                    "<title>Pride And Prejudice</title>" & _
                    "</book>")
        Dim root As XmlElement = doc.DocumentElement

        ' Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel")

        Console.WriteLine("Display the modified XML...")
        Console.WriteLine(doc.InnerXml)
    End Sub
End Class
```  
  
```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{
    public static void Main()
    {
        var doc = new XmlDocument();
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +
                    "<title>Pride And Prejudice</title>" +
                    "</book>");
        XmlElement root = doc.DocumentElement;

        // Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel");

        Console.WriteLine("Display the modified XML...");
        Console.WriteLine(doc.InnerXml);
    }
}
```

<span data-ttu-id="94626-108">Následující příklad ukazuje nový atribut, který je vytvářen pomocí metody **CreateAttribute** .</span><span class="sxs-lookup"><span data-stu-id="94626-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="94626-109">Pak zobrazuje atribut přidaný do kolekce atributů prvku **Book** pomocí metody **SetAttributeNode** .</span><span class="sxs-lookup"><span data-stu-id="94626-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>

<span data-ttu-id="94626-110">S ohledem na následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="94626-110">Given the following XML:</span></span>
  
```xml
<book genre='novel' ISBN='1-861001-57-5'>
<title>Pride And Prejudice</title>
</book>
```

<span data-ttu-id="94626-111">Vytvořte nový atribut a poskytněte mu hodnotu:</span><span class="sxs-lookup"><span data-stu-id="94626-111">create a new attribute and give it a value:</span></span>

```vb
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")
attr.Value = "WorldWide Publishing"
```

```csharp
XmlAttribute attr = doc.CreateAttribute("publisher");
attr.Value = "WorldWide Publishing";
```

<span data-ttu-id="94626-112">a připojte jej k elementu:</span><span class="sxs-lookup"><span data-stu-id="94626-112">and attach it to the element:</span></span>

```vb
doc.DocumentElement.SetAttributeNode(attr)
```

```csharp
doc.DocumentElement.SetAttributeNode(attr);
```

<span data-ttu-id="94626-113">**Output**</span><span class="sxs-lookup"><span data-stu-id="94626-113">**Output**</span></span>

```xml
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">
<title>Pride And Prejudice</title>
</book>
```

<span data-ttu-id="94626-114">Úplný vzorek kódu najdete na adrese <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="94626-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>

<span data-ttu-id="94626-115">Můžete také vytvořit uzel **XmlAttribute** a použít metody **InsertBefore** nebo **InsertAfter** k umístění do příslušné pozice v kolekci.</span><span class="sxs-lookup"><span data-stu-id="94626-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="94626-116">Pokud je v kolekci atributů již přítomen atribut se stejným názvem, existující uzel **XmlAttribute** je odebrán z kolekce a je vložen nový uzel **XmlAttribute** .</span><span class="sxs-lookup"><span data-stu-id="94626-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="94626-117">To funguje stejným způsobem jako metoda **SetAttributes** .</span><span class="sxs-lookup"><span data-stu-id="94626-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="94626-118">Tyto metody přebírají jako parametr existující uzel jako referenční bod pro provádění **InsertBefore** a **InsertAfter**.</span><span class="sxs-lookup"><span data-stu-id="94626-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="94626-119">Pokud neposkytnete referenční uzel určující, kam vložit nový uzel, je výchozím nastavením pro metodu **InsertAfter** vložení nového uzlu na začátek kolekce.</span><span class="sxs-lookup"><span data-stu-id="94626-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="94626-120">Výchozí pozice pro **InsertBefore**, pokud není k dispozici žádný uzel odkazu, je na konci kolekce.</span><span class="sxs-lookup"><span data-stu-id="94626-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>

<span data-ttu-id="94626-121">Pokud jste vytvořili **XmlNamedNodeMap** atributů, můžete přidat atribut podle názvu pomocí metody <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="94626-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A> method.</span></span> <span data-ttu-id="94626-122">Další informace najdete v tématu [kolekce uzlů v NamedNodeMaps a NodeLists](node-collections-in-namednodemaps-and-nodelists.md).</span><span class="sxs-lookup"><span data-stu-id="94626-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](node-collections-in-namednodemaps-and-nodelists.md).</span></span>

## <a name="default-attributes"></a><span data-ttu-id="94626-123">Výchozí atributy</span><span class="sxs-lookup"><span data-stu-id="94626-123">Default attributes</span></span>

<span data-ttu-id="94626-124">Vytvoříte-li prvek, který je deklarován jako výchozí atribut, je vytvořen nový výchozí atribut s výchozí hodnotou v souboru XML model DOM (Document Object Model) (DOM) a připojen k elementu.</span><span class="sxs-lookup"><span data-stu-id="94626-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="94626-125">V tuto chvíli se vytvoří i podřízených uzlů výchozích atributů.</span><span class="sxs-lookup"><span data-stu-id="94626-125">The child nodes of the default attribute are also created at this time.</span></span>

## <a name="attribute-child-nodes"></a><span data-ttu-id="94626-126">Podřízené uzly atributu</span><span class="sxs-lookup"><span data-stu-id="94626-126">Attribute child nodes</span></span>

<span data-ttu-id="94626-127">Hodnota uzlu atributu se bude jednat o své podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="94626-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="94626-128">Existují pouze dva typy platných podřízených uzlů: uzly **XmlText** a uzly **XmlEntityReference** .</span><span class="sxs-lookup"><span data-stu-id="94626-128">There are only two types of valid child nodes: **XmlText** nodes and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="94626-129">Jedná se o podřízené uzly v tom smyslu, že metody jako **hodnotu FirstChild** a **LastChild** je zpracovávají jako podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="94626-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="94626-130">Toto rozlišení atributu s podřízenými uzly je důležité při pokusu o odebrání atributů nebo podřízených uzlů atributů.</span><span class="sxs-lookup"><span data-stu-id="94626-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="94626-131">Další informace naleznete v tématu [Odebrání atributů z uzlu elementu v modelu DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="94626-131">For more information, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="94626-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94626-132">See also</span></span>

- [<span data-ttu-id="94626-133">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="94626-133">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
