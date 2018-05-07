---
title: Zachování dvojice název hodnota (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: 6d842adb1e21a7744f03f4a7e7fb0785ffb6a119
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>Zachování dvojice název hodnota (Visual Basic)
Mnoho aplikací mít ke správě informací, která je lepší je ponechat jako dvojice název/hodnota. Tyto informace mohou být informace o konfiguraci nebo globální nastavení. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsahuje některé metody, které usnadňují zachovat sadu dvojice název/hodnota. Buď můžete zachovat informace jako atributy nebo jako sada podřízené elementy.  
  
 Jeden rozdíl mezi zajistit přitom ochranu informací jako atributy nebo jako podřízené prvky je, že atributy mít omezení, může být pouze jeden atribut s konkrétním názvem pro daný element. Toto omezení se nevztahuje na podřízené elementy.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue a SetElementValue  
 Tyto dvě metody, které usnadňují zachování páry název/hodnota jsou <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> a <xref:System.Xml.Linq.XElement.SetElementValue%2A>. Tyto dvě metody mají podobnou sémantiku jako.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> můžete přidávat, upravovat nebo odebírat atributy elementu.  
  
-   Když zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> název atributu, který ještě neexistuje, metoda vytvoří nový atribut a přidá ji do zadaného elementu.  
  
-   Když zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existující atribut a některé zadaný obsah, obsah atributu se nahradí zadaný obsah.  
  
-   Když zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atribut a zadejte hodnotu null pro obsah, atribut je odebrán z jeho nadřazený objekt.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A> můžete přidávat, upravovat nebo odebírat podřízené elementy elementu.  
  
-   Když zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem podřízený element, který ještě neexistuje, metoda vytvoří nového elementu a přidá ji do zadaného elementu.  
  
-   Když zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího elementu a některé zadaný obsah, obsah elementu se nahradí zadaný obsah.  
  
-   Když zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího elementu a zadejte hodnotu null pro obsah, element je odebrán z jeho nadřazený objekt.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří element se žádné atributy. Poté použije <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metoda vytvořit a spravovat seznam dvojic název hodnota.  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří element s žádné podřízené elementy. Poté použije <xref:System.Xml.Linq.XElement.SetElementValue%2A> metoda vytvořit a spravovat seznam dvojic název hodnota.  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>  
 [Úprava XML stromů (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
