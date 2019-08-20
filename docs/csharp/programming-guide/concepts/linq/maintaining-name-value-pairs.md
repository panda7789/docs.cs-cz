---
title: Udržování párů název-hodnota (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 9c42a154a4c3ed1463e428faab4c7d33197ef4a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591703"
---
# <a name="maintaining-namevalue-pairs-c"></a>Udržování párů název/hodnota (C#)
Mnoho aplikací musí uchovávat informace, které jsou nejvhodnější pro páry název/hodnota. Tyto informace můžou být konfigurační informace nebo globální nastavení. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obsahuje některé metody, které usnadňují zachování sady párů název/hodnota. Tyto informace můžete zachovat jako atributy nebo jako sadu podřízených prvků.  
  
 Jeden rozdíl mezi uchováváním informací jako atributů nebo jako podřízených elementů je, že atributy mají omezení, že může existovat pouze jeden atribut s určitým názvem pro element. Toto omezení se nevztahuje na podřízené prvky.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue a SetElementValue  
 Existují dvě metody, které pomáhají zachovat páry název/hodnota <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> jsou <xref:System.Xml.Linq.XElement.SetElementValue%2A>a. Tyto dvě metody mají podobnou sémantiku.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>může přidat, upravit nebo odebrat atributy prvku.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem atributu, který neexistuje, metoda vytvoří nový atribut a přidá jej do zadaného elementu.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a s určitým zadaným obsahem, obsah atributu se nahradí zadaným obsahem.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a pro obsah zadáte null, atribut se odebere z nadřazeného objektu.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>může přidat, upravit nebo odebrat podřízené prvky elementu.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem podřízeného prvku, který neexistuje, metoda vytvoří nový prvek a přidá jej do zadaného elementu.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a s určitým zadaným obsahem, obsah elementu se nahradí zadaným obsahem.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a pro obsah zadáte null, element je odebrán z nadřazeného prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří prvek bez atributů. Pak pomocí <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metody vytvoří a udržuje seznam párů název/hodnota.  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří prvek bez podřízených elementů. Pak pomocí <xref:System.Xml.Linq.XElement.SetElementValue%2A> metody vytvoří a udržuje seznam párů název/hodnota.  
  
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
- [Úprava stromů XML (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
