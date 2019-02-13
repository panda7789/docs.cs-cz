---
title: Zařazování řetězců
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4640d37ad6c30746e203c26c2c1cd71eb70e7579
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218564"
---
# <a name="marshaling-strings"></a>Zařazování řetězců
Zkopíruje řetězec parametrů, jejich konverze z formátu rozhraní .NET Framework (Unicode) na nespravované formátu (ANSI), v případě potřeby vyvolání platformy. Protože spravované řetězce jsou neměnné, vyvolání platformy nekopíruje je zpět z nespravované paměti pro spravované paměti při návratu funkce.  
  
 V následující tabulce jsou uvedeny možnosti zařazování pro řetězce, popisuje jejich využití a získáte odkaz na odpovídající vzorku rozhraní .NET Framework.  
  
|String|Popis|Ukázka|  
|------------|-----------------|------------|  
|Podle hodnoty.|Předá řetězců jako parametry in.|[MsgBox](msgbox-sample.md)|  
|Jako výsledek.|Vrátí hodnotu řetězce z nespravovaného kódu.|[Řetězce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Podle odkazu.|Předá řetězců jako vstup a výstup parametry s využitím <xref:System.Text.StringBuilder>.|[Vyrovnávací paměti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))|  
|Ve struktuře podle hodnoty.|Předá řetězce ve struktuře, která je parametr In.|[Struktury](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))|  
|Ve struktuře odkazem **(char\*)**.|Předá řetězce ve struktuře je vstupně-výstupní parametr. Nespravovaná funkce očekává ukazatel na znak vyrovnávací paměť a velikost vyrovnávací paměti je členem struktury.|[Řetězce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Ve struktuře odkazem **(char[])**.|Předá řetězce ve struktuře je vstupně-výstupní parametr. Nespravovaná funkce očekává vyrovnávací pamětí vloženého znaku.|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Ve třídě podle hodnoty **(char\*)**.|Předá řetězce do třídy (třídy je vstupně-výstupní parametr). Nespravovaná funkce očekává ukazatel do vyrovnávací paměti pro znaky.|[OpenFileDlg](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w5tyztk9(v=vs.100))|  
|Ve třídě podle hodnoty **(char[])**.|Předá řetězce do třídy (třídy je vstupně-výstupní parametr). Nespravovaná funkce očekává vyrovnávací pamětí vloženého znaku.|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Jako pole řetězců podle hodnoty.|Je vytvořeno pole řetězců, který je předán podle hodnoty.|[Pole](marshaling-different-types-of-arrays.md)|  
|Jako pole struktury, které obsahují řetězce podle hodnoty.|Vytvoří pole struktur, které obsahují řetězce a pole je předán podle hodnoty.|[Pole](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Viz také:
- [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)
- [Zařazování tříd, struktur a sjednocení](marshaling-classes-structures-and-unions.md)
- [Zařazování různých typů polí](marshaling-different-types-of-arrays.md)
- [Různé ukázky zařazování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
