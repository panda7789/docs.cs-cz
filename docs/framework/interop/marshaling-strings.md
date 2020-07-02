---
title: Zařazování řetězců
description: Přečtěte si, jak zařazovat řetězce. Viz možnosti pro zařazování řetězců podle hodnoty nebo odkazu, jako výsledek, ve struktuře nebo třídě podle hodnoty nebo odkazu a dalších.
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
ms.openlocfilehash: 0be5a5817bd92c5be6b701200a74650ef9de1955
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621480"
---
# <a name="marshaling-strings"></a>Zařazování řetězců
Vyvolání platformy kopíruje parametry řetězce a v případě potřeby je převádí z formátu .NET Framework (Unicode) do nespravovaného formátu (ANSI). Vzhledem k tomu, že spravované řetězce jsou neměnné, volání platformy je nekopíruje zpátky z nespravované paměti do spravované paměti, když funkce vrátí.  
  
 Následující tabulka uvádí možnosti zařazování pro řetězce, popisuje jejich použití a poskytuje odkaz na odpovídající ukázku .NET Framework.  
  
|Řetězec|Popis|Ukázka|  
|------------|-----------------|------------|  
|Podle hodnoty.|Předá řetězce jako v parametrech.|[MsgBox](msgbox-sample.md)|  
|Jako výsledek.|Vrátí řetězce z nespravovaného kódu.|[Řetězce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Odkazem.|Předává řetězce jako vstupně-výstupní parametry pomocí <xref:System.Text.StringBuilder> .|[Vyrovnávací paměti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))|  
|Ve struktuře podle hodnoty.|Předá řetězce ve struktuře, která je v parametru.|[Struktury](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))|  
|Ve struktuře podle odkazu **(Char \* )**.|Předá řetězce ve struktuře, která je parametrem in/out. Nespravovaná funkce očekává ukazatel na vyrovnávací paměť znaků a velikost vyrovnávací paměti je členem struktury.|[Řetězce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Ve struktuře podle odkazu **(Char [])**.|Předá řetězce ve struktuře, která je parametrem in/out. Nespravovaná funkce očekává vyrovnávací paměť vloženého znaku.|[OSINFO –](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Ve třídě podle hodnoty **(Char \* )**.|Předá řetězce ve třídě (třída je parametrem in/out). Nespravovaná funkce očekává ukazatel na vyrovnávací paměť znaků.|[Openfiledlg –](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w5tyztk9(v=vs.100))|  
|Ve třídě podle hodnoty **(Char [])**.|Předá řetězce ve třídě (třída je parametrem in/out). Nespravovaná funkce očekává vyrovnávací paměť vloženého znaku.|[OSINFO –](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Jako pole řetězců podle hodnoty.|Vytvoří pole řetězců, které je předáno hodnotou.|[Pole](marshaling-different-types-of-arrays.md)|  
|Jako pole struktury, které obsahují řetězce podle hodnoty.|Vytvoří pole struktury obsahující řetězce a pole je předáno hodnotou.|[Pole](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Viz také:

- [Výchozí zařazování pro řetězce](default-marshaling-for-strings.md)
- [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)
- [Zařazování tříd, struktur a sjednocení](marshaling-classes-structures-and-unions.md)
- [Zařazování různých typů polí](marshaling-different-types-of-arrays.md)
- [Různé vzorky zařazování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
