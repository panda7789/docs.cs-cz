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
# <a name="maintaining-namevalue-pairs-c"></a>Udržování párů názvů a hodnot (C#)
Mnoho aplikací musí udržovat informace, které je nejlépe uchovávat jako dvojice název/hodnota. Tyto informace mohou být informace o konfiguraci nebo globální nastavení. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obsahuje některé metody, které usnadňují zachování sady párů název/hodnota. Informace můžete uchovávat jako atributy nebo jako sadu podřízených prvků.  
  
 Jeden rozdíl mezi zachování informace jako atributy nebo jako podřízené prvky je, že atributy mají omezení, které může být pouze jeden atribut s určitým názvem pro prvek. Toto omezení se nevztahuje na podřízené prvky.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue a SetElementValue  
 Dvě metody, které usnadňují zachování dvojice <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> <xref:System.Xml.Linq.XElement.SetElementValue%2A>název/hodnota jsou a . Tyto dvě metody mají podobnou sémantiku.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>můžete přidat, upravit nebo odebrat atributy prvku.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem atributu, který neexistuje, metoda vytvoří nový atribut a přidá jej do zadaného prvku.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a s určitým zadaným obsahem, obsah atributu bude nahrazen zadaným obsahem.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> s názvem existujícího atributu a zadáte hodnotu null pro obsah, bude atribut odebrán z nadřazeného atributu.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>můžete přidat, upravit nebo odebrat podřízené prvky prvku.  
  
- Pokud voláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem podřízeného prvku, který neexistuje, metoda vytvoří nový prvek a přidá jej do zadaného prvku.  
  
- Pokud zavoláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a s určitým zadaným obsahem, obsah prvku je nahrazen zadaným obsahem.  
  
- Pokud voláte <xref:System.Xml.Linq.XElement.SetElementValue%2A> s názvem existujícího prvku a zadejte hodnotu null pro obsah, prvek je odebrán z nadřazeného prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří prvek bez atributů. Potom používá <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metodu k vytvoření a udržovat seznam párů název/hodnota.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří prvek bez podřízených prvků. Potom používá <xref:System.Xml.Linq.XElement.SetElementValue%2A> metodu k vytvoření a udržovat seznam párů název/hodnota.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
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

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [Úprava meziřazených stromů XML (LINQ na XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
