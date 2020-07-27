---
title: Zachování párů název-hodnota (C#)
description: LINQ to XML obsahuje metody, které usnadňují udržování párů název/hodnota, a to buď jako atributy, nebo jako sadu podřízených elementů.
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 92a45d160cbb1ef470d93bf740d0b6f584681e72
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165272"
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="6ba96-103">Udržování párů název/hodnota (C#)</span><span class="sxs-lookup"><span data-stu-id="6ba96-103">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="6ba96-104">Mnoho aplikací musí uchovávat informace, které jsou nejvhodnější pro páry název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="6ba96-104">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="6ba96-105">Tyto informace můžou být konfigurační informace nebo globální nastavení.</span><span class="sxs-lookup"><span data-stu-id="6ba96-105">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6ba96-106">obsahuje některé metody, které usnadňují zachování sady párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="6ba96-106">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="6ba96-107">Tyto informace můžete zachovat jako atributy nebo jako sadu podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="6ba96-107">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="6ba96-108">Jeden rozdíl mezi uchováváním informací jako atributů nebo jako podřízených elementů je, že atributy mají omezení, že může existovat pouze jeden atribut s určitým názvem pro element.</span><span class="sxs-lookup"><span data-stu-id="6ba96-108">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="6ba96-109">Toto omezení se nevztahuje na podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="6ba96-109">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="6ba96-110">SetAttributeValue a SetElementValue</span><span class="sxs-lookup"><span data-stu-id="6ba96-110">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="6ba96-111">Existují dvě metody, které pomáhají zachovat páry název/hodnota jsou <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> a <xref:System.Xml.Linq.XElement.SetElementValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="6ba96-111">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="6ba96-112">Tyto dvě metody mají podobnou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="6ba96-112">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="6ba96-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>může přidat, upravit nebo odebrat atributy prvku.</span><span class="sxs-lookup"><span data-stu-id="6ba96-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="6ba96-114">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem atributu, který neexistuje, metoda vytvoří nový atribut a přidá jej do zadaného elementu.</span><span class="sxs-lookup"><span data-stu-id="6ba96-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="6ba96-115">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a s určitým zadaným obsahem, obsah atributu se nahradí zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="6ba96-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="6ba96-116">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a pro obsah zadáte null, atribut se odebere z nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="6ba96-116">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="6ba96-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A>může přidat, upravit nebo odebrat podřízené prvky elementu.</span><span class="sxs-lookup"><span data-stu-id="6ba96-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="6ba96-118">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem podřízeného prvku, který neexistuje, metoda vytvoří nový prvek a přidá jej do zadaného elementu.</span><span class="sxs-lookup"><span data-stu-id="6ba96-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="6ba96-119">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a s určitým zadaným obsahem, obsah elementu se nahradí zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="6ba96-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="6ba96-120">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a pro obsah zadáte null, element je odebrán z nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="6ba96-120">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ba96-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ba96-121">Example</span></span>  
 <span data-ttu-id="6ba96-122">Následující příklad vytvoří prvek bez atributů.</span><span class="sxs-lookup"><span data-stu-id="6ba96-122">The following example creates an element with no attributes.</span></span> <span data-ttu-id="6ba96-123">Pak pomocí <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metody vytvoří a udržuje seznam párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="6ba96-123">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="6ba96-124">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6ba96-124">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="6ba96-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ba96-125">Example</span></span>  
 <span data-ttu-id="6ba96-126">Následující příklad vytvoří prvek bez podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="6ba96-126">The following example creates an element with no child elements.</span></span> <span data-ttu-id="6ba96-127">Pak pomocí <xref:System.Xml.Linq.XElement.SetElementValue%2A> metody vytvoří a udržuje seznam párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="6ba96-127">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="6ba96-128">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6ba96-128">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ba96-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ba96-129">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="6ba96-130">Úpravy stromů XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6ba96-130">Modifying XML Trees (LINQ to XML) (C#)</span></span>](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
