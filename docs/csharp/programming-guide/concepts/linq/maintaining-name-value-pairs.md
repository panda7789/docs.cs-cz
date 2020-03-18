---
title: Udržování párů název-hodnota (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 9c42a154a4c3ed1463e428faab4c7d33197ef4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591703"
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="32803-102">Udržování párů názvů a hodnot (C#)</span><span class="sxs-lookup"><span data-stu-id="32803-102">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="32803-103">Mnoho aplikací musí udržovat informace, které je nejlépe uchovávat jako dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="32803-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="32803-104">Tyto informace mohou být informace o konfiguraci nebo globální nastavení.</span><span class="sxs-lookup"><span data-stu-id="32803-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="32803-105">obsahuje některé metody, které usnadňují zachování sady párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="32803-105">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="32803-106">Informace můžete uchovávat jako atributy nebo jako sadu podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="32803-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="32803-107">Jeden rozdíl mezi zachování informace jako atributy nebo jako podřízené prvky je, že atributy mají omezení, které může být pouze jeden atribut s určitým názvem pro prvek.</span><span class="sxs-lookup"><span data-stu-id="32803-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="32803-108">Toto omezení se nevztahuje na podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="32803-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="32803-109">SetAttributeValue a SetElementValue</span><span class="sxs-lookup"><span data-stu-id="32803-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="32803-110">Dvě metody, které usnadňují zachování dvojice <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> <xref:System.Xml.Linq.XElement.SetElementValue%2A>název/hodnota jsou a .</span><span class="sxs-lookup"><span data-stu-id="32803-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="32803-111">Tyto dvě metody mají podobnou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="32803-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="32803-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>můžete přidat, upravit nebo odebrat atributy prvku.</span><span class="sxs-lookup"><span data-stu-id="32803-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="32803-113">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem atributu, který neexistuje, metoda vytvoří nový atribut a přidá jej do zadaného prvku.</span><span class="sxs-lookup"><span data-stu-id="32803-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="32803-114">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a s určitým zadaným obsahem, obsah atributu bude nahrazen zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="32803-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="32803-115">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a zadáte hodnotu null pro obsah, bude atribut odebrán z nadřazeného atributu.</span><span class="sxs-lookup"><span data-stu-id="32803-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="32803-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A>můžete přidat, upravit nebo odebrat podřízené prvky prvku.</span><span class="sxs-lookup"><span data-stu-id="32803-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="32803-117">Pokud voláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem podřízeného prvku, který neexistuje, metoda vytvoří nový prvek a přidá jej do zadaného prvku.</span><span class="sxs-lookup"><span data-stu-id="32803-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="32803-118">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a s určitým zadaným obsahem, obsah prvku je nahrazen zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="32803-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="32803-119">Pokud voláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a zadejte hodnotu null pro obsah, prvek je odebrán z nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="32803-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32803-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="32803-120">Example</span></span>  
 <span data-ttu-id="32803-121">Následující příklad vytvoří prvek bez atributů.</span><span class="sxs-lookup"><span data-stu-id="32803-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="32803-122">Potom používá <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metodu k vytvoření a udržovat seznam párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="32803-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="32803-123">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="32803-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="32803-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="32803-124">Example</span></span>  
 <span data-ttu-id="32803-125">Následující příklad vytvoří prvek bez podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="32803-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="32803-126">Potom používá <xref:System.Xml.Linq.XElement.SetElementValue%2A> metodu k vytvoření a udržovat seznam párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="32803-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="32803-127">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="32803-127">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32803-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="32803-128">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="32803-129">Úprava meziřazených stromů XML (LINQ na XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="32803-129">Modifying XML Trees (LINQ to XML) (C#)</span></span>](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
