---
title: Požadavky na verzi a aktualizace pro vývojáře v jazyce C#
description: Zavedení nových funkcí jazyků do knihovny může mít vliv na kód, který ho používá.
ms.topic: reference
ms.date: 09/19/2018
ms.openlocfilehash: f7db7c79792d04bcf592bc1858e1f0f05cb34402
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88268124"
---
# <a name="version-and-update-considerations-for-c-developers"></a>Požadavky na verzi a aktualizace pro vývojáře v jazyce C#

Kompatibilita je velice důležitým cílem při přidávání nových funkcí do jazyka C#. Ve většině případů může být existující kód znovu zkompilován s novou verzí kompilátoru bez jakýchkoli potíží.

Při přijímání nových funkcí jazyka v knihovně se může vyžadovat lepší péče. Je možné, že vytváříte novou knihovnu s funkcemi nalezenými v nejnovější verzi a potřebujete zajistit, aby aplikace sestavené pomocí předchozích verzí kompilátoru mohla použít. Nebo můžete upgradovat existující knihovnu a mnoho uživatelů možná ještě neupgradoval verze. Při rozhodování o přijímání nových funkcí je potřeba vzít v úvahu dvě varianty kompatibility: kompatibilní se zdrojem a binární kompatibilní.

## <a name="binary-compatible-changes"></a>Binární kompatibilní změny

Změny v knihovně jsou **binární, kompatibilní** s tím, že aktualizovaná knihovna může být použita bez nutnosti znovu sestavovat aplikace a knihovny, které ji používají. Závislá sestavení není nutné znovu sestavit, ani nejsou vyžadovány žádné změny zdrojového kódu. Změny binární kompatibility jsou také kompatibilní se zdroji.

## <a name="source-compatible-changes"></a>Změny kompatibilní se zdrojem

Změny v knihovně jsou **kompatibilní se zdrojem** , když aplikace a knihovny, které používají vaši knihovnu, nevyžadují změny zdrojového kódu, ale zdroj musí být znovu zkompilován z důvodu správné správné správné verze.

## <a name="incompatible-changes"></a>Nekompatibilní změny

Pokud změna není kompatibilní se **zdrojem** ani v **binárním**formátu, jsou v závislých knihovnách a aplikacích vyžadovány změny zdrojového kódu společně s opětovnou kompilací.

## <a name="evaluate-your-library"></a>Vyhodnocení knihovny

Tyto koncepce kompatibility mají vliv na veřejné a chráněné deklarace pro vaši knihovnu, nikoli na její interní implementaci. Interní přijímání nových funkcí je v **binárním**formátu vždycky kompatibilní.  

**Binární kompatibilní** změny poskytují novou syntaxi, která generuje stejný zkompilovaný kód pro veřejné deklarace jako starší syntaxi. Například změna metody na člena Expression-těle je **binární kompatibilní** změna:

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

Změny **kompatibilní se zdrojem** zavádí syntaxi, která mění zkompilovaný kód pro veřejný člen, ale způsobem, který je kompatibilní s existujícími lokalitami volání. Například změna signatury metody z parametru podle hodnoty na `in` parametr podle odkazu je kompatibilní se zdrojem, ale není kompatibilní s binárním:

Původní kód:

```csharp
public double CalculateSquare(double value) => value * value;
```

Nový kód:

```csharp
public double CalculateSquare(in double value) => value * value;
```

Poznámky k [novinkám](index.md) , pokud zavádíte funkci, která má vliv na veřejné deklarace, jsou kompatibilní se zdrojem nebo binární kompatibilní.
