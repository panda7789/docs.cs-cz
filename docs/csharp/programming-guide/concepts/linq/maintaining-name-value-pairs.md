---
title: Zachování dvojic název hodnota (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 28c01ce17881ffe7e8fcc35e2c23dec85d50955d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43657984"
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="39274-102">Zachování dvojic název/hodnota (C#)</span><span class="sxs-lookup"><span data-stu-id="39274-102">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="39274-103">Mnoho aplikací nutné udržovat informace, které nejlépe se ukládají jako dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="39274-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="39274-104">Tyto informace mohou být informace o konfiguraci nebo globální nastavení.</span><span class="sxs-lookup"><span data-stu-id="39274-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="39274-105"> obsahuje některé metody, které usnadňují zachovat sadu párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="39274-105"> contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="39274-106">Buď můžete zachovat informace jako atributy nebo sadu podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="39274-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="39274-107">Jedním z rozdílů mezi chrání informace jako atributy nebo podřízené prvky je, že atributy obsahují omezení, že může existovat pouze jeden atribut s konkrétním názvem pro daný element.</span><span class="sxs-lookup"><span data-stu-id="39274-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="39274-108">Toto omezení se nevztahuje na podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="39274-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="39274-109">SetAttributeValue a SetElementValue</span><span class="sxs-lookup"><span data-stu-id="39274-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="39274-110">Dvě metody, které usnadňují uchování páry název/hodnota jsou <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> a <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="39274-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="39274-111">Tyto dvě metody mají podobnou sémantikou.</span><span class="sxs-lookup"><span data-stu-id="39274-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="39274-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> můžete přidat, upravit nebo odebrat atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="39274-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
-   <span data-ttu-id="39274-113">Při volání <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem atributu, který ještě neexistuje, metoda vytvoří nový atribut a přidá jej do zadaného prvku.</span><span class="sxs-lookup"><span data-stu-id="39274-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="39274-114">Při volání <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a s některými zadaný obsahu, obsah atributu nahrazují se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="39274-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="39274-115">Při volání <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atribut a zadejte hodnotu null pro obsah, atribut se odebere ze svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="39274-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="39274-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> můžete přidat, upravit nebo odebrat podřízené prvky prvku.</span><span class="sxs-lookup"><span data-stu-id="39274-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
-   <span data-ttu-id="39274-117">Při volání <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem podřízený element, který ještě neexistuje, metoda vytvoří nový prvek a přidá jej do zadaného prvku.</span><span class="sxs-lookup"><span data-stu-id="39274-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="39274-118">Při volání <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a s některými zadaný obsahu, obsah elementu se nahradí se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="39274-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="39274-119">Při volání <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a zadejte hodnotu null pro obsah, elementu se odebere ze svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="39274-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39274-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="39274-120">Example</span></span>  
 <span data-ttu-id="39274-121">Následující příklad vytvoří element se žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="39274-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="39274-122">Poté použije <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metodu pro vytvoření a správa seznamu párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="39274-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22);  
root.SetAttributeValue("Left", 20);  
root.SetAttributeValue("Bottom", 122);  
root.SetAttributeValue("Right", 300);  
root.SetAttributeValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
  
// Replace the value of Top.  
root.SetAttributeValue("Top", 10);  
Console.WriteLine(root);  
  
// Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="39274-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="39274-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="39274-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="39274-124">Example</span></span>  
 <span data-ttu-id="39274-125">Následující příklad vytvoří element se žádné podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="39274-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="39274-126">Poté použije <xref:System.Xml.Linq.XElement.SetElementValue%2A> metodu pro vytvoření a správa seznamu párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="39274-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22);  
root.SetElementValue("Left", 20);  
root.SetElementValue("Bottom", 122);  
root.SetElementValue("Right", 300);  
root.SetElementValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Replace the value of Top.  
root.SetElementValue("Top", 10);  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Remove DefaultColor.  
root.SetElementValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="39274-127">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="39274-127">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39274-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="39274-128">See Also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>  
- [<span data-ttu-id="39274-129">Změna stromů XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="39274-129">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
