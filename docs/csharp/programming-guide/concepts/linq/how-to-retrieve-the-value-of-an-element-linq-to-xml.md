---
title: Jak načíst hodnotu elementu (LINQ to XML) (C#)
description: Přečtěte si, jak získat hodnotu prvků. Podívejte se na příklady použití přetypování řetězců, celočíselného přetypování a vlastnosti Value.
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: eb750927d74c3068d7ab06caba9835110bd77a09
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301538"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Jak načíst hodnotu elementu (LINQ to XML) (C#)

Tento článek ukazuje, jak získat hodnotu prvků. Existují dva hlavní způsoby, jak získat hodnotu:

- Přetypování <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> na požadovaný typ. Operátor explicitního převodu pak převede obsah elementu nebo atributu na zadaný typ a přiřadí ho k proměnné.

- Použijte <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti nebo <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> . Tuto hodnotu můžete také nastavit pomocí těchto vlastností.

V jazyce C# je přetypování všeobecně lepším přístupem. Pokud přetypování elementu nebo atributu na typ hodnoty s možnou hodnotou null, kód je jednodušší zapsat při načítání hodnoty prvku (nebo atributu), který může nebo nemusí existovat. [Poslední příklad](#element-might-not-exist-example) v tomto článku ukazuje, že přetypování je jednodušší v případě, kdy element pravděpodobně neexistuje. Nemůžete však nastavit obsah elementu prostřednictvím přetypování, jak můžete prostřednictvím <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> Vlastnosti.  
  
## <a name="string-cast-example"></a>Příklad přetypování řetězců  
 Chcete-li načíst hodnotu prvku, přetypování <xref:System.Xml.Linq.XElement> objektu na požadovaný typ. Můžete přetypovat element na řetězec následujícím způsobem:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a>Příklad přetypování typu Integer  
 Prvky lze také přetypovat na jiné typy než řetězec. Například pokud máte prvek, který obsahuje celé číslo, můžete jej přetypovat na `int` , jak je znázorněno v následujícím kódu:  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje operátory explicitního přetypování pro následující datové typy: `string` ,,,, `bool` `bool?` `int` `int?` , `uint` , `uint?` , `long` , `long?` , `ulong` , `ulong?` , `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` ,, `DateTime` , `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,, a.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje stejné operátory přetypování pro <xref:System.Xml.Linq.XAttribute> objekty.  
  
## <a name="value-property-example"></a>Vlastnost hodnoty – příklad  
 Vlastnost můžete použít <xref:System.Xml.Linq.XElement.Value%2A> k načtení obsahu prvku:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a>Element nemusí existovat příklad.
 Někdy se pokusíte načíst hodnotu prvku, i když si nejste jistí, jestli existuje. V takovém případě, když přiřadíte předaný element na odkazový typ s možnou hodnotou null nebo typ hodnoty s možnou hodnotou null, pokud element neexistuje, přiřazená proměnná je nastavena na `null` . Následující kód ukazuje, že pokud element může nebo nemusí existovat, je snazší použít přetypování, než aby bylo možné použít <xref:System.Xml.Linq.XElement.Value%2A> vlastnost.  
  
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
  
 Obecně lze psát jednodušší kód při použití přetypování k načtení obsahu prvků a atributů.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
