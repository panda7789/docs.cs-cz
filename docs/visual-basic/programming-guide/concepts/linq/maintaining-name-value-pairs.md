---
title: Zachování dvojice název hodnota (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: 6d842adb1e21a7744f03f4a7e7fb0785ffb6a119
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646874"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a><span data-ttu-id="58027-102">Zachování dvojice název hodnota (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58027-102">Maintaining Name/Value Pairs (Visual Basic)</span></span>
<span data-ttu-id="58027-103">Mnoho aplikací mít ke správě informací, která je lepší je ponechat jako dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="58027-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="58027-104">Tyto informace mohou být informace o konfiguraci nebo globální nastavení.</span><span class="sxs-lookup"><span data-stu-id="58027-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="58027-105"> obsahuje některé metody, které usnadňují zachovat sadu dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="58027-105"> contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="58027-106">Buď můžete zachovat informace jako atributy nebo jako sada podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="58027-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="58027-107">Jeden rozdíl mezi zajistit přitom ochranu informací jako atributy nebo jako podřízené prvky je, že atributy mít omezení, může být pouze jeden atribut s konkrétním názvem pro daný element.</span><span class="sxs-lookup"><span data-stu-id="58027-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="58027-108">Toto omezení se nevztahuje na podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="58027-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="58027-109">SetAttributeValue a SetElementValue</span><span class="sxs-lookup"><span data-stu-id="58027-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="58027-110">Tyto dvě metody, které usnadňují zachování páry název/hodnota jsou <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> a <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="58027-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="58027-111">Tyto dvě metody mají podobnou sémantiku jako.</span><span class="sxs-lookup"><span data-stu-id="58027-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="58027-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> můžete přidávat, upravovat nebo odebírat atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="58027-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
-   <span data-ttu-id="58027-113">Když zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> název atributu, který ještě neexistuje, metoda vytvoří nový atribut a přidá ji do zadaného elementu.</span><span class="sxs-lookup"><span data-stu-id="58027-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="58027-114">Když zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existující atribut a některé zadaný obsah, obsah atributu se nahradí zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="58027-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="58027-115">Když zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atribut a zadejte hodnotu null pro obsah, atribut je odebrán z jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="58027-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="58027-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> můžete přidávat, upravovat nebo odebírat podřízené elementy elementu.</span><span class="sxs-lookup"><span data-stu-id="58027-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
-   <span data-ttu-id="58027-117">Když zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem podřízený element, který ještě neexistuje, metoda vytvoří nového elementu a přidá ji do zadaného elementu.</span><span class="sxs-lookup"><span data-stu-id="58027-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="58027-118">Když zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího elementu a některé zadaný obsah, obsah elementu se nahradí zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="58027-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="58027-119">Když zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího elementu a zadejte hodnotu null pro obsah, element je odebrán z jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="58027-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58027-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="58027-120">Example</span></span>  
 <span data-ttu-id="58027-121">Následující příklad vytvoří element se žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="58027-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="58027-122">Poté použije <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metoda vytvořit a spravovat seznam dvojic název hodnota.</span><span class="sxs-lookup"><span data-stu-id="58027-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="58027-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="58027-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="58027-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="58027-124">Example</span></span>  
 <span data-ttu-id="58027-125">Následující příklad vytvoří element s žádné podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="58027-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="58027-126">Poté použije <xref:System.Xml.Linq.XElement.SetElementValue%2A> metoda vytvořit a spravovat seznam dvojic název hodnota.</span><span class="sxs-lookup"><span data-stu-id="58027-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="58027-127">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="58027-127">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58027-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="58027-128">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>  
 [<span data-ttu-id="58027-129">Úprava XML stromů (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58027-129">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
