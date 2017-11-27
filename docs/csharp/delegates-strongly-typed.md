---
title: "Delegáti silného typu"
description: "Naučte se používat delegáty obecných typů deklarovat vlastních typů, při vytváření funkce, které vyžadují delegáti."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 467ba18f8e032b9b3b8f480d4b10c92d0d7ba3b9
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="strongly-typed-delegates"></a>Delegáti silného typu

[Předchozí](delegate-class.md)

V předchozím článku jste viděli, vytvořit konkrétní delegáta typy pomocí `delegate` – klíčové slovo. 

Abstraktní třída delegáta poskytují infrastrukturu pro volné párování a volání. Konkrétní typy delegáta stát mnohem užitečnější přijetí a vynucování bezpečnost typů pro metody, které jsou přidány do seznamu vyvolání delegáta objektu. Při použití `delegate` – klíčové slovo a definice typu konkrétní delegáta, kompilátor vygeneruje těchto metod.

V praxi by docházelo k vytvoření nového delegáta typy kdykoli budete potřebovat podpis jinou metodu. Tento pracovní může získat zdlouhavé po uplynutí určité doby. Všechny nové funkce, které vyžaduje nové typy delegáta.

Naštěstí to není nutné. Rozhraní .NET Core obsahuje několik typů, které můžete opakovaně použít vždy, když potřebují delegovat typy. Jedná se o [Obecné](programming-guide/generics/index.md) definice tak můžou deklarovat přizpůsobení, pokud budete potřebovat nové metoda deklarace. 

První z těchto typů je <xref:System.Action> typ a více změn:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

`in` Modifikátor na argument obecného typu je popsaná v článku na kovariance.

Existují variace `Action` delegáta, který obsahovat až 16 argumenty, jako například <xref:System.Action%6016>.
Je důležité, aby tyto definice použít jiné obecné argumenty pro každou z argumentů delegáta: který poskytuje maximální flexibilitu. Metoda argumenty, které nemusí být, ale může být stejného typu.

Použijte jednu z `Action` typy pro jakýkoli typ delegáta, který má typ vrácené hodnoty void.

Rozhraní framework také obsahuje několik typů obecný delegát, které jsou vhodné pro typy delegáta, které vrací hodnoty:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

`out` Modifikátor na argument obecného typu výsledek je popsaná v článku na kovariance.

Existují variace `Func` delegovat s až 16 vstupní argumenty, jako <xref:System.Func%6017>.
Typ výsledku je vždy poslední parametr typu ve všech `Func` deklarace podle konvence.

Použijte jednu z `Func` typy pro jakýkoli typ delegáta, který vrací hodnotu.

Je taky speciální <xref:System.Predicate%601> typ pro delegáta, který vrátí testu na jednu hodnotu:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Můžete si všimnout, pro žádné `Predicate` typu, strukturálně ekvivalentní `Func` typ existuje třeba:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Může si myslíte, že jsou tyto dva typy ekvivalentní. Nejsou.
Tyto dvě proměnné nelze použít zcela zaměnitelným významem. Proměnná jeden typ nelze přiřadit, v případě druhého typu. Systém typů jazyka C# používá názvy definovaných typů, není strukturu.

Všechny tyto typ delegáta, který definice v základní knihovny .NET by měl znamenat, že není nutné definovat nový typ delegáta pro jakékoli nové funkce vytvoříte, které vyžaduje delegáti. Tyto obecné definice by měl poskytovat všechny delegát typy, které je nutné v části většině případů. Můžete jednoduše vytvořit instanci jedním z těchto typů s požadovaný typ parametry. V případě algoritmy, které můžete provést obecný můžete využít tyto delegáti jako obecné typy. 

To by měl ušetřit čas a minimalizovat počet nových typů, které je potřeba vytvořit za účelem práce s delegáti.

V další článek zobrazí se několik běžných vzorů pro práci s Delegáti v praxi.

[Další](delegates-patterns.md)
