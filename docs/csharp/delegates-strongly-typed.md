---
title: Delegáty se silnými typy
description: Zjistěte, jak používat obecné typy delegátů k deklarování vlastních typů při vytváření funkce vyžadující delegáty.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 798e8b597389bc99d10e587ec417a4e717f28abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146200"
---
# <a name="strongly-typed-delegates"></a>Delegáty se silnými typy

[Předchozí](delegate-class.md)

V předchozím článku jste viděli, že pomocí `delegate` klíčového slova vytvoříte konkrétní typy delegátů.

Abstraktní Delegate třídy poskytují infrastrukturu pro volné párování a vyvolání. Konkrétní Delegate typy mnohem užitečnější tím, že zahrnuje a vynucuje bezpečnost typů pro metody, které jsou přidány do seznamu vyvolání pro objekt delegáta. Při použití `delegate` klíčového slova a definovat konkrétní typ delegáta, kompilátor generuje tyto metody.

V praxi by to vedlo k vytvoření nových typů delegátů, kdykoli potřebujete podpis jiné metody. Tato práce by mohla dostat únavné po čase. Každá nová funkce vyžaduje nové typy delegátů.

Naštěstí to není nutné. Rozhraní .NET Core framework obsahuje několik typů, které můžete znovu použít vždy, když potřebujete typy delegátů. Jedná [se o obecné](programming-guide/generics/index.md) definice, takže můžete deklarovat vlastní nastavení, když potřebujete nové deklarace metody.

První z těchto typů <xref:System.Action> je typ a několik variant:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

Modifikátor `in` na argument obecného typu je popsán v článku o kovariance.

Existují varianty delegáta, `Action` které obsahují až 16 <xref:System.Action%6016>argumentů, například .
Je důležité, aby tyto definice používat různé obecné argumenty pro každý z delegáta argumenty: To vám dává maximální flexibilitu. Argumenty metody nemusí být, ale může být stejný typ.

Použijte jeden `Action` z typů pro všechny typy delegáta, který má prázdný návratový typ.

Rámec také obsahuje několik obecných typů delegátů, které můžete použít pro typy delegátů, které vracejí hodnoty:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

Modifikátor `out` argumentu typu typu výsledek je popsán v článku o kovariance.

Existují varianty delegáta `Func` s až 16 vstupní <xref:System.Func%6017>argumenty, jako je například .
Typ výsledku je vždy poslední parametr typu `Func` ve všech deklaracích podle konvence.

Použijte jeden `Func` z typů pro libovolný typ delegáta, který vrací hodnotu.

K dispozici je také specializovaný<xref:System.Predicate%601>
zadejte delegáta, který vrátí test na jednu hodnotu:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Můžete si všimnout, že pro `Predicate` `Func` jakýkoli typ existuje strukturálně ekvivalentní typ Například:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Možná si myslíte, že tyto dva typy jsou ekvivalentní. Nejsou.
Tyto dvě proměnné nelze zaměnit. Proměnné jednoho typu nelze přiřadit jiný typ. Systém typu C# používá názvy definovaných typů, nikoli strukturu.

Všechny tyto definice typu delegáta v základní knihovně .NET by měly znamenat, že není nutné definovat nový typ delegáta pro žádnou novou funkci, kterou vytvoříte a která vyžaduje delegáty. Tyto obecné definice by měly poskytovat všechny typy delegátů, které potřebujete ve většině situací. Můžete jednoduše vytvořit konkretizovat jeden z těchto typů s požadovanými parametry typu. V případě algoritmů, které mohou být obecné, tyto delegáty lze použít jako obecné typy.

To by mělo ušetřit čas a minimalizovat počet nových typů, které je třeba vytvořit, aby bylo možné pracovat s delegáty.

V dalším článku uvidíte několik běžných vzorů pro práci s delegáty v praxi.

[Další](delegates-patterns.md)
