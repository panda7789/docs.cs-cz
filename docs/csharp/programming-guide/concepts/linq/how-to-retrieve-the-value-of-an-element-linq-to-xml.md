---
title: "Postupy: načtení hodnoty elementu (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ceb803eff68f72378ca195120ed96990d62d3593
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Postupy: načtení hodnoty elementu (technologie LINQ to XML) (C#)
Toto téma ukazuje, jak má být získána hodnota elementů. Chcete-li to provést dvěma způsoby. Jedním ze způsobů je přetypovat <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> na požadovaný typ. Explicitní převod operátor potom převede obsah elementu nebo atributu na zadaný typ a přiřadí ji k vaše proměnná. Alternativně můžete použít <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost nebo <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> vlastnost.  
  
 Pomocí C# ale přetypování je obecně lepší přístup. Pokud přetypovat element nebo atribut na typ s možnou hodnotou Null, kód je jednodušší zápis při načítání hodnoty elementu (nebo atributu), který může nebo nemusí existovat. Poslední příklad v tomto tématu ukazuje to. Však nelze nastavit obsah elementu přetypování, protože můžete prostřednictvím <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
 K načtení hodnoty elementu, je právě přetypovat <xref:System.Xml.Linq.XElement> objekt, který má požadovaný typ. Element na řetězec, můžete vždy přetypovat následujícím způsobem:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Příklad  
 Můžete také přetypování elementy na typy jiné než řetězec. Například pokud máte elementu, který obsahuje celé číslo, vám může vysílat `int`, jak je znázorněno v následujícím kódu:  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje operátory explicitní přetypování pro následující typy dat: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`a `GUID?`.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje stejné operátory přetypování pro <xref:System.Xml.Linq.XAttribute> objekty.  
  
## <a name="example"></a>Příklad  
 Můžete použít <xref:System.Xml.Linq.XElement.Value%2A> vlastnost můžete načíst obsah elementu:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");   
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Příklad  
 Někdy pokusu načíst hodnotu elementu, i když si nejste jisti, že existuje. V takovém případě přiřadíte-li převedena element na typ s možnou hodnotou Null (buď `string` nebo jeden z typů s povolenou hodnotou Null v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), pokud element neexistuje přiřazená proměnná je nastavená pouze na `null`. Následující kód ukazuje, že pokud element může nebo nemusí existovat, je jednodušší použít přetypování než k použijte <xref:System.Xml.Linq.XElement.Value%2A> vlastnost.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 Tento kód vytvoří následující výstup:  
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 Obecně platí můžete napsat kód jednodušší při použití přetypování můžete načíst obsah elementů a atributů.  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML osy (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
