---
title: "Zachování dvojice název hodnota (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e2743b7ce09db2ec2695c04eeef631a33fa2c289
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a><span data-ttu-id="52d98-102">Zachování dvojice název hodnota (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52d98-102">Maintaining Name/Value Pairs (Visual Basic)</span></span>
<span data-ttu-id="52d98-103">Mnoho aplikací mít ke správě informací, která je lepší je ponechat jako dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="52d98-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="52d98-104">Tyto informace mohou být informace o konfiguraci nebo globální nastavení.</span><span class="sxs-lookup"><span data-stu-id="52d98-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="52d98-105">obsahuje některé metody, které usnadňují zachovat sadu dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="52d98-105"> contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="52d98-106">Buď můžete zachovat informace jako atributy nebo jako sada podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="52d98-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="52d98-107">Jeden rozdíl mezi zajistit přitom ochranu informací jako atributy nebo jako podřízené prvky je, že atributy mít omezení, může být pouze jeden atribut s konkrétním názvem pro daný element.</span><span class="sxs-lookup"><span data-stu-id="52d98-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="52d98-108">Toto omezení se nevztahuje na podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="52d98-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="52d98-109">SetAttributeValue a SetElementValue</span><span class="sxs-lookup"><span data-stu-id="52d98-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="52d98-110">Tyto dvě metody, které usnadňují zachování páry název/hodnota jsou <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> a <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="52d98-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="52d98-111">Tyto dvě metody mají podobnou sémantiku jako.</span><span class="sxs-lookup"><span data-stu-id="52d98-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="52d98-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>můžete přidávat, upravovat nebo odebírat atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="52d98-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
-   <span data-ttu-id="52d98-113">Když zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> název atributu, který ještě neexistuje, metoda vytvoří nový atribut a přidá ji do zadaného elementu.</span><span class="sxs-lookup"><span data-stu-id="52d98-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="52d98-114">Když zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existující atribut a některé zadaný obsah, obsah atributu se nahradí zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="52d98-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="52d98-115">Když zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atribut a zadejte hodnotu null pro obsah, atribut je odebrán z jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="52d98-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="52d98-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A>můžete přidávat, upravovat nebo odebírat podřízené elementy elementu.</span><span class="sxs-lookup"><span data-stu-id="52d98-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
-   <span data-ttu-id="52d98-117">Když zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem podřízený element, který ještě neexistuje, metoda vytvoří nového elementu a přidá ji do zadaného elementu.</span><span class="sxs-lookup"><span data-stu-id="52d98-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="52d98-118">Když zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího elementu a některé zadaný obsah, obsah elementu se nahradí zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="52d98-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="52d98-119">Když zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího elementu a zadejte hodnotu null pro obsah, element je odebrán z jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="52d98-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52d98-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="52d98-120">Example</span></span>  
 <span data-ttu-id="52d98-121">Následující příklad vytvoří element se žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="52d98-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="52d98-122">Poté použije <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metoda vytvořit a spravovat seznam dvojic název hodnota.</span><span class="sxs-lookup"><span data-stu-id="52d98-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="52d98-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="52d98-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="52d98-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="52d98-124">Example</span></span>  
 <span data-ttu-id="52d98-125">Následující příklad vytvoří element s žádné podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="52d98-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="52d98-126">Poté použije <xref:System.Xml.Linq.XElement.SetElementValue%2A> metoda vytvořit a spravovat seznam dvojic název hodnota.</span><span class="sxs-lookup"><span data-stu-id="52d98-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="52d98-127">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="52d98-127">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="52d98-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="52d98-128">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>  
 [<span data-ttu-id="52d98-129">Úprava XML stromů (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52d98-129">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
