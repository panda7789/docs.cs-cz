---
title: Zachování dvojic název a hodnota
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: b8c9487330239e7e6365055d5f08a02f2dbb0e37
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796142"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a><span data-ttu-id="8c158-102">Udržování párů název/hodnota (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c158-102">Maintaining Name/Value Pairs (Visual Basic)</span></span>
<span data-ttu-id="8c158-103">Mnoho aplikací musí uchovávat informace, které jsou nejvhodnější pro páry název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="8c158-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="8c158-104">Tyto informace můžou být konfigurační informace nebo globální nastavení.</span><span class="sxs-lookup"><span data-stu-id="8c158-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="8c158-105">obsahuje některé metody, které usnadňují zachování sady párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="8c158-105">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="8c158-106">Tyto informace můžete zachovat jako atributy nebo jako sadu podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="8c158-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="8c158-107">Jeden rozdíl mezi uchováváním informací jako atributů nebo jako podřízených elementů je, že atributy mají omezení, že může existovat pouze jeden atribut s určitým názvem pro element.</span><span class="sxs-lookup"><span data-stu-id="8c158-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="8c158-108">Toto omezení se nevztahuje na podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="8c158-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="8c158-109">SetAttributeValue a SetElementValue</span><span class="sxs-lookup"><span data-stu-id="8c158-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="8c158-110">Existují dvě metody, které pomáhají zachovat páry název/hodnota <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> jsou <xref:System.Xml.Linq.XElement.SetElementValue%2A>a.</span><span class="sxs-lookup"><span data-stu-id="8c158-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="8c158-111">Tyto dvě metody mají podobnou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="8c158-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="8c158-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>může přidat, upravit nebo odebrat atributy prvku.</span><span class="sxs-lookup"><span data-stu-id="8c158-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="8c158-113">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem atributu, který neexistuje, metoda vytvoří nový atribut a přidá jej do zadaného elementu.</span><span class="sxs-lookup"><span data-stu-id="8c158-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="8c158-114">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a s určitým zadaným obsahem, obsah atributu se nahradí zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="8c158-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="8c158-115">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a pro obsah zadáte null, atribut se odebere z nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="8c158-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="8c158-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A>může přidat, upravit nebo odebrat podřízené prvky elementu.</span><span class="sxs-lookup"><span data-stu-id="8c158-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="8c158-117">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem podřízeného prvku, který neexistuje, metoda vytvoří nový prvek a přidá jej do zadaného elementu.</span><span class="sxs-lookup"><span data-stu-id="8c158-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="8c158-118">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a s určitým zadaným obsahem, obsah elementu se nahradí zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="8c158-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="8c158-119">Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a pro obsah zadáte null, element je odebrán z nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="8c158-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c158-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c158-120">Example</span></span>  
 <span data-ttu-id="8c158-121">Následující příklad vytvoří prvek bez atributů.</span><span class="sxs-lookup"><span data-stu-id="8c158-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="8c158-122">Pak pomocí <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metody vytvoří a udržuje seznam párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="8c158-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22)  
root.SetAttributeValue("Left", 20)  
root.SetAttributeValue("Bottom", 122)  
root.SetAttributeValue("Right", 300)  
root.SetAttributeValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
  
' Replace the value of Top.  
root.SetAttributeValue("Top", 10)  
Console.WriteLine(root)  
  
' Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="8c158-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8c158-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="8c158-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c158-124">Example</span></span>  
 <span data-ttu-id="8c158-125">Následující příklad vytvoří prvek bez podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="8c158-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="8c158-126">Pak pomocí <xref:System.Xml.Linq.XElement.SetElementValue%2A> metody vytvoří a udržuje seznam párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="8c158-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22)  
root.SetElementValue("Left", 20)  
root.SetElementValue("Bottom", 122)  
root.SetElementValue("Right", 300)  
root.SetElementValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Replace the value of Top.  
root.SetElementValue("Top", 10)  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Remove DefaultColor.  
root.SetElementValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="8c158-127">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8c158-127">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8c158-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c158-128">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="8c158-129">Úprava stromů XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c158-129">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
