---
title: Jak načíst hodnotu prvku (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: c4bb78e937fe0de08242923cdd7cd638abf571c7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805830"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Jak načíst hodnotu prvku (LINQ do XML) (C#)

Tento článek ukazuje, jak získat hodnotu prvků. Existují dva hlavní způsoby, jak získat hodnotu:

- Přetypovat <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> nebo na požadovaný typ. Explicitní operátor převodu pak převede obsah prvku nebo atributu na zadaný typ a přiřadí jej proměnné.

- Použijte <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti nebo. <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> Můžete také nastavit hodnotu pomocí těchto vlastností.

S C#, casting je obecně lepší přístup. Pokud přetypování prvku nebo atributu na typ hodnoty s možnou hodnotou, kterou lze použít s nulou, je jednodušší zapisovat kód při načítání hodnoty elementu (nebo atributu), který může nebo nemusí existovat. [Poslední příklad](#element-might-not-exist-example) v tomto článku ukazuje, že obsazení je jednodušší v případě, kdy prvek nemusí existovat. Však nelze nastavit obsah prvku prostřednictvím přetypování, jak můžete prostřednictvím <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti.  
  
## <a name="string-cast-example"></a>Příklad přetypování řetězců  
 Chcete-li načíst hodnotu <xref:System.Xml.Linq.XElement> prvku, přetypujte objekt na požadovaný typ. Prvek můžete přetypovat do řetězce takto:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a>Příklad podčísla obsazení  
 Prvky můžete také přetypovat na jiné typy než řetězec. Například pokud máte prvek, který obsahuje celé číslo, můžete `int`přetypovat do , jak je znázorněno v následujícím kódu:  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje explicitní operátory přetypádky pro `int?` `uint`následující `uint?` `long`datové `long?` `ulong` `ulong?`typy: `float` `float?` `double` `double?` `decimal` `decimal?` `DateTime` `DateTime?` `string` `bool`, , `bool?` `int`, , , , , , , , , , , , , `TimeSpan`, `TimeSpan?`, `GUID`, , , a `GUID?`.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje stejné operátory <xref:System.Xml.Linq.XAttribute> přetypádku pro objekty.  
  
## <a name="value-property-example"></a>Příklad vlastnosti hodnoty  
 <xref:System.Xml.Linq.XElement.Value%2A> Vlastnost můžete použít k načtení obsahu prvku:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a>Prvek pravděpodobně neexistuje příklad
 Někdy se pokusíte načíst hodnotu prvku, i když si nejste jisti, pokud existuje. V tomto případě při přiřazení odevzdaného prvku k typu odkazu s možnou hodnotou s možnou hodnotou `null`null nebo typu hodnoty s možnou hodnotou, pokud prvek neexistuje, je přiřazená proměnná nastavena na . Následující kód ukazuje, že když prvek může nebo nemusí existovat, je <xref:System.Xml.Linq.XElement.Value%2A> jednodušší použít přetypování než použít vlastnost.  
  
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
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 Obecně můžete napsat jednodušší kód při použití přetypování k načtení obsahu prvků a atributů.  
  
## <a name="see-also"></a>Viz také

- [LINQ na osy XML (C#)](./linq-to-xml-axes-overview.md)
