---
title: Delegáty se silnými typy
description: Naučte se používat obecné typy delegátů k deklaraci vlastních typů při vytváření funkce vyžadující delegáty.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: efdbef39d0e6bf2f07cde2c9621cec173e921752
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037360"
---
# <a name="strongly-typed-delegates"></a>Delegáty se silnými typy

[Předchozí](delegate-class.md)

V předchozím článku jste viděli, že vytvoříte konkrétní typy delegátů pomocí klíčového slova `delegate`. 

Abstraktní třída delegáta poskytuje infrastrukturu pro volné spojování a volání. Konkrétní typy delegátů jsou mnohem užitečnější přechodu a vynucování bezpečnosti typů pro metody, které jsou přidány do seznamu vyvolání pro objekt delegáta. Při použití klíčového slova `delegate` a definování konkrétního typu delegáta kompilátor vygeneruje tyto metody.

V praxi by to vedlo k vytváření nových typů delegátů, kdykoli potřebujete jiný podpis metody. Tato práce může po čase obdržet únavné. Každá nová funkce vyžaduje nové typy delegátů.

Naštěstí to není nutné. Rozhraní .NET Core Framework obsahuje několik typů, které můžete opakovaně používat, kdykoli potřebujete typy delegátů. Jedná se o [Obecné](programming-guide/generics/index.md) definice, abyste mohli deklarovat vlastní nastavení, když budete potřebovat nové deklarace metod. 

První z těchto typů je <xref:System.Action> typ a několik variant:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

Modifikátor `in` v argumentu obecného typu je popsaný v článku o kovarianci.

Existují varianty `Action` delegáta, které obsahují až 16 argumentů, jako je například <xref:System.Action%6016>.
Je důležité, aby tyto definice pro každý z argumentů delegáta používaly různé obecné argumenty: to zajišťuje maximální flexibilitu. Argumenty metody nemusí být, ale mohou být stejného typu.

Použijte jeden z `Action` typů pro libovolný typ delegáta, který má typ vrácené hodnoty void.

Rozhraní zahrnuje také několik generických typů delegátů, které lze použít pro typy delegátů, které vracejí hodnoty:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

Modifikátor `out` v argumentu výsledek obecného typu je popsaný v článku o kovarianci.

Existují odchylky `Func` delegáta s až 16 vstupními argumenty, jako je například <xref:System.Func%6017>.
Typ výsledku je vždy parametr posledního typu ve všech deklaracích `Func` podle konvence.

Pro libovolný typ delegáta, který vrací hodnotu, použijte jeden z `Func` typů.

K dispozici je také specializované <xref:System.Predicate%601> 
typ pro delegáta, který vrátí test na jednu hodnotu:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Můžete si všimnout, že u jakéhokoli typu `Predicate` existuje strukturální ekvivalentní `Func` typ například:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Možná si myslíte, že tyto dva typy jsou ekvivalentní. Nejsou.
Tyto dvě proměnné nelze použít zaměnitelné. Proměnné jednoho typu se nedá přiřadit jiný typ. Systém C# typů používá názvy definovaných typů, nikoli strukturu.

Všechny tyto definice typů delegátů v knihovně .NET Core by měly znamenat, že nemusíte definovat nový typ delegáta pro každou nově vytvořenou funkci, která vyžaduje delegáty. Tyto obecné definice by měly ve většině případů poskytovat všechny typy delegátů, které potřebujete. Můžete jednoduše vytvořit instanci jednoho z těchto typů s požadovanými parametry typu. V případě algoritmů, které lze nastavit jako obecné, lze tyto delegáty použít jako obecné typy. 

To by mělo ušetřit čas a minimalizovat počet nových typů, které je třeba vytvořit, aby bylo možné pracovat s delegáty.

V dalším článku uvidíte několik běžných vzorů pro práci s delegáty v praxi.

[Next](delegates-patterns.md)
