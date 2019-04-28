---
title: Delegáty se silnými typy
description: Další informace o použití obecné typy delegátů pro deklaraci vlastní typy při vytváření funkce vyžadující delegátů.
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646654"
---
# <a name="strongly-typed-delegates"></a>Delegáty se silnými typy

[Předchozí](delegate-class.md)

V předchozím článku jste viděli, vytvořit konkrétní delegáta typů pomocí `delegate` – klíčové slovo. 

Abstraktní třída delegáta poskytování infrastruktury pro volné párování a vyvolání. Ve středu a bezpečnost typů pro metody, které se přidají do seznamu vyvolání pro objekt delegáta vynucování stane mnohem užitečnější konkrétní typy delegátů. Při použití `delegate` – klíčové slovo a definovat delegáta konkrétní typ, kompilátor vygeneruje tyto metody.

V praxi to vede k vytváření nového delegáta typů pokaždé, když potřebujete podpis jinou metodu. Tato práce může únavné po uplynutí určité doby. Všechny nové funkce, které vyžaduje nové typy delegátů.

Naštěstí to není nutné. .NET Core framework obsahuje několik typů, které můžete znovu použít pokaždé, když potřebujete typy delegátů. Jedná se o [obecný](programming-guide/generics/index.md) definice, takže je možné deklarovat vlastní nastavení, když budete potřebovat nové deklarace metody. 

První z těchto typů je <xref:System.Action> typu a používat několik variant:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

`in` Modifikátor argument obecného typu je popsaná v článku na kovariance.

Existují variace `Action` delegáta, který obsahuje až 16 argumenty, jako <xref:System.Action%6016>.
Je důležité, že tyto definice pomocí různých obecných argumentů pro jednotlivé argumenty delegáta: Který poskytuje maximální flexibilitu. Argumenty metody nemusí být, ale může být stejného typu.

Použijte jednu z `Action` typy pro libovolný typ delegáta, který má typ vrácené hodnoty void.

Rozhraní také obsahuje několik typů obecného delegátu, které můžete použít pro typy delegátů, které vracejí hodnoty:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

`out` Modifikátor argument obecného typu výsledku je popsaná v článku na kovariance.

Existují variace `Func` delegáta s až 16 vstupní argumenty, jako <xref:System.Func%6017>.
Typ výsledku je vždy poslední parametr typu ve všech `Func` deklarace podle konvence.

Použijte jednu z `Func` typy pro jakýkoli typ delegáta, který vrací hodnotu.

Je také specializované <xref:System.Predicate%601> 
typ delegáta, který vrací test na jednu hodnotu:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Můžete si všimnout, které pro všechny `Predicate` typ, strukturálně ekvivalentní `Func` typ existuje. například:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Možná myslíte, že tyto dva typy jsou ekvivalentní. Nejsou.
Tyto dvě proměnné nelze používat Zaměnitelně. Jiný typ nelze přiřadit proměnné typu jeden. C# Názvy definované typy, nikoli struktura používá systém typů.

Všechny tyto typ delegáta, který by měl definice v základní knihovně .NET znamená, že není potřeba definovat nový typ delegáta pro jakékoli nové funkce můžete vytvořit, které vyžaduje delegátů. Tyto obecné definice by měly poskytnout všechny delegáta typy, které je třeba v části většinu situací. Můžete jednoduše vytvořit instanci jednoho z těchto typů s parametry požadovaného typu. V případě algoritmů, které mohou být provedeny obecný tyto delegáty slouží jako obecné typy. 

To by měl šetří čas a minimalizovat počet nových typů, které je potřeba vytvořit za účelem práce s delegátů.

V následujícím článku uvidíte několik běžných vzorů pro práci s Delegáti v praxi.

[Next](delegates-patterns.md)
