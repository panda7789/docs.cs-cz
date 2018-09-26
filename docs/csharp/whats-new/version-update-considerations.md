---
title: Verze a aktualizace důležité informace pro vývojáře v C#
description: Představení nových funkcí jazyků v knihovně může mít vliv na kód, který ji používá.
ms.date: 09/19/2018
ms.openlocfilehash: 56685422e2c73dcca25acbdccb3a77a8de9df775
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199928"
---
# <a name="version-and-update-considerations-for-c-developers"></a>Verze a aktualizace důležité informace pro vývojáře v C#

Kompatibilita je velmi důležité cílem přidávání nových funkcí jazyka C#. V téměř všech případech se můžete znovu zkompilovat existujícího kódu pomocí nové verze kompilátoru bez jakýkoli problém.

Větší péči se může vyžadovat při přijetí nové funkce jazyků v knihovně. Může vytvářet nové knihovny s funkcemi, které jsou k dispozici v nejnovější verzi a potřebujete zajistit aplikací vytvořených pomocí předchozí verze kompilátoru ji použít. Nebo upgradu existující knihovnu a mnoho z vašich uživatelů nemusí upgradu verze ještě. Při provádění rozhodnutí o zavedení nových funkcí, je potřeba vzít v úvahu dvě varianty kompatibility: zdroj kompatibilní a binární kompatibilní.

## <a name="binary-compatible-changes"></a>Binární kompatibilní změny

Změny knihovny jsou **binární kompatibilní** při aktualizované knihovny je možné bez nutnosti opětovného sestavení aplikací a knihoven, které ji používají. Závislá sestavení nejsou nutné znovu sestavit ani jsou nutné změny zdrojového kódu. Binární kompatibilní změny jsou i změny kompatibilní zdroj.

## <a name="source-compatible-changes"></a>Kompatibilní změny zdroje

Změny knihovny jsou **zdroj kompatibilní** při aplikací a knihoven, které používají knihovnu nevyžadují změny zdrojového kódu, ale zdroj musí zopakovat na novou verzi fungovat správně.

## <a name="incompatible-changes"></a>Nekompatibilní změny

Pokud změna není ani **zdroj kompatibilní** ani **binární kompatibilní**, jsou nezbytné změny zdrojového kódu společně s rekompilace závislé knihovny a aplikace.

## <a name="evaluate-your-library"></a>Vyhodnocení knihovny

Tyto koncepty kompatibility vliv na deklarace veřejné a chráněné knihovny, nikoli jeho vnitřní implementace. Interně přijímat žádné nové funkce jsou vždy **binární kompatibilní**.  

**Binární kompatibilní** změny poskytují novou syntaxi, která generuje stejný zkompilovaný kód pro veřejné deklarace jako starší syntaxe. Například změna metody pro člena s výrazem v těle je **binární kompatibilní** změnit:

Původní kód:

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

Nový kód:

```csharp
public double CalculateSquare(double value) => value * value;
```

**Zdroj kompatibilní** změny zavedou syntaxe, která se mění zkompilovaný kód pro veřejný člen, ale v způsobem, který je kompatibilní s existující lokalit volání. Například změna podpisu metody z parametrem hodnotu do `in` odkazem. parametr je zdroj kompatibilní, ale nikoli binární kompatibilní:

Původní kód:

```csharp
public double CalculateSquare(double value) => value * value;
```

Nový kód:

```csharp
public double CalculateSquare(in double value) => value * value;
```

[Novinky](index.md) články Poznámka: Pokud představení funkce, která má vliv na veřejné deklarace kompatibilní zdroj nebo binární kompatibilní.