---
title: Důležité informace o verzi a aktualizaci pro vývojáře jazyka C#
description: Zavedení nových funkcí jazyků v knihovně může mít vliv na kód, který ji používá.
ms.date: 09/19/2018
ms.openlocfilehash: 3ffe2f6fd64a391fddf28233dccb022c95851884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399383"
---
# <a name="version-and-update-considerations-for-c-developers"></a>Důležité informace o verzi a aktualizaci pro vývojáře jazyka C#

Kompatibilita je velmi důležitý cíl jako nové funkce jsou přidány do jazyka C#. Téměř ve všech případech lze existující kód znovu zkompilovat s novou verzí kompilátoru bez problémů.

Při zavádění nových jazykových funkcí v knihovně může být vyžadována větší péče. Možná vytváříte novou knihovnu s funkcemi, které se nacházejí v nejnovější verzi, a potřebujete zajistit, aby aplikace vytvořené pomocí předchozích verzí kompilátoru mohly používat. Nebo je možné, že upgradujete existující knihovnu a mnoho uživatelů ještě nemá inovované verze. Při rozhodování o přijetí nových funkcí budete muset zvážit dvě varianty kompatibility: kompatibilitu se zdrojem a binární kompatibilitu.

## <a name="binary-compatible-changes"></a>Binární kompatibilní změny

Změny v knihovně jsou **binární kompatibilní,** pokud lze aktualizovanou knihovnu použít bez opětovného sestavení aplikací a knihoven, které ji používají. Závislé sestavení není nutné znovu sestavit, ani nejsou vyžadovány žádné změny zdrojového kódu. Binární kompatibilní změny jsou také změny kompatibilní se zdrojem.

## <a name="source-compatible-changes"></a>Změny kompatibilní se zdrojem

Změny v knihovně jsou **kompatibilní se zdrojem,** pokud aplikace a knihovny, které používají vaši knihovnu, nevyžadují změny zdrojového kódu, ale zdroj musí být znovu zkompilován proti nové verzi, aby fungoval správně.

## <a name="incompatible-changes"></a>Nekompatibilní změny

Pokud změna není ani **zdrojkompatibilní,** ani **binární kompatibilní**, změny zdrojového kódu spolu s rekompilace jsou vyžadovány v závislých knihovnách a aplikacích.

## <a name="evaluate-your-library"></a>Vyhodnocení knihovny

Tyto koncepty kompatibility ovlivňují veřejné a chráněné deklarace pro vaši knihovnu, nikoli její interní implementaci. Přijetí všech nových funkcí interně jsou vždy **binární kompatibilní**.  

**Binární kompatibilní** změny poskytují novou syntaxi, která generuje stejný kompilovaný kód pro veřejná prohlášení jako starší syntaxe. Například změna metody na člen s výrazem je **binární kompatibilní** změna:

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

**Změny kompatibilní se zdrojem** zavádějí syntaxi, která mění zkompilovaný kód pro veřejného člena, ale způsobem, který je kompatibilní s existujícími weby volání. Například změna podpisu metody z parametru `in` podle hodnoty na parametr podle odkazu je kompatibilní se zdrojem, ale není kompatibilní s binárním souborem:

Původní kód:

```csharp
public double CalculateSquare(double value) => value * value;
```

Nový kód:

```csharp
public double CalculateSquare(in double value) => value * value;
```

[Co je nového](index.md) články na vědomí, pokud zavedení funkce, která ovlivňuje veřejné deklarace je zdroj kompatibilní nebo binární kompatibilní.
