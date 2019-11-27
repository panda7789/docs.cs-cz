---
title: Zachování dvojic název a hodnota
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: ed9c7f0aae2fe646cd723321f45455f89dd7c370
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331668"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>Udržování párů název/hodnota (Visual Basic)
Mnoho aplikací musí uchovávat informace, které jsou nejvhodnější pro páry název/hodnota. Tyto informace můžou být konfigurační informace nebo globální nastavení. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsahuje některé metody, které usnadňují zachování sady párů název/hodnota. Tyto informace můžete zachovat jako atributy nebo jako sadu podřízených prvků.  
  
 Jeden rozdíl mezi uchováváním informací jako atributů nebo jako podřízených elementů je, že atributy mají omezení, že může existovat pouze jeden atribut s určitým názvem pro element. Toto omezení se nevztahuje na podřízené prvky.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue a SetElementValue  
 Tyto dvě metody, které pomáhají zachovat páry název/hodnota, jsou <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> a <xref:System.Xml.Linq.XElement.SetElementValue%2A>. Tyto dvě metody mají podobnou sémantiku.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> může přidat, upravit nebo odebrat atributy prvku.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem atributu, který neexistuje, metoda vytvoří nový atribut a přidá jej do zadaného elementu.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a s určitým zadaným obsahem, obsah atributu se nahradí zadaným obsahem.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a pro obsah zadáte hodnotu null, atribut se odebere z nadřazeného objektu.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A> může přidat, upravit nebo odebrat podřízené prvky elementu.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem podřízeného prvku, který neexistuje, metoda vytvoří nový prvek a přidá jej do zadaného elementu.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a s určitým zadaným obsahem, obsah elementu se nahradí zadaným obsahem.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a pro obsah zadáte hodnotu null, prvek je odebrán z nadřazeného objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří prvek bez atributů. Pak pomocí metody <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> vytvoří a udržuje seznam párů název/hodnota.  
  
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
 Následující příklad vytvoří prvek bez podřízených elementů. Pak pomocí metody <xref:System.Xml.Linq.XElement.SetElementValue%2A> vytvoří a udržuje seznam párů název/hodnota.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [Úprava stromů XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
