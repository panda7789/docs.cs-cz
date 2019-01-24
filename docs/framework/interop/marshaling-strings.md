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
ms.openlocfilehash: bc4f40ab954a3bb31e0b55aad8c00ed2ee63f6c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514891"
---
# <a name="marshaling-strings"></a>Zařazování řetězců
Zkopíruje řetězec parametrů, jejich konverze z formátu rozhraní .NET Framework (Unicode) na nespravované formátu (ANSI), v případě potřeby vyvolání platformy. Protože spravované řetězce jsou neměnné, vyvolání platformy nekopíruje je zpět z nespravované paměti pro spravované paměti při návratu funkce.  
  
 V následující tabulce jsou uvedeny možnosti zařazování pro řetězce, popisuje jejich využití a získáte odkaz na odpovídající vzorku rozhraní .NET Framework.  
  
|String|Popis|Ukázka|  
|------------|-----------------|------------|  
|Podle hodnoty.|Předá řetězců jako parametry in.|[MsgBox](msgbox-sample.md)|  
|Jako výsledek.|Vrátí hodnotu řetězce z nespravovaného kódu.|[Řetězce](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Podle odkazu.|Předá řetězců jako vstup a výstup parametry s využitím <xref:System.Text.StringBuilder>.|[Vyrovnávací paměti](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100))|  
|Ve struktuře podle hodnoty.|Předá řetězce ve struktuře, která je parametr In.|[Struktury](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100))|  
|Ve struktuře odkazem **(char\*)**.|Předá řetězce ve struktuře je vstupně-výstupní parametr. Nespravovaná funkce očekává ukazatel na znak vyrovnávací paměť a velikost vyrovnávací paměti je členem struktury.|[Řetězce](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Ve struktuře odkazem **(char[])**.|Předá řetězce ve struktuře je vstupně-výstupní parametr. Nespravovaná funkce očekává vyrovnávací pamětí vloženého znaku.|[OSInfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Ve třídě podle hodnoty **(char\*)**.|Předá řetězce do třídy (třídy je vstupně-výstupní parametr). Nespravovaná funkce očekává ukazatel do vyrovnávací paměti pro znaky.|[OpenFileDlg](https://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75(v=vs.100))|  
|Ve třídě podle hodnoty **(char[])**.|Předá řetězce do třídy (třídy je vstupně-výstupní parametr). Nespravovaná funkce očekává vyrovnávací pamětí vloženého znaku.|[OSInfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Jako pole řetězců podle hodnoty.|Je vytvořeno pole řetězců, který je předán podle hodnoty.|[Pole](marshaling-different-types-of-arrays.md)|  
|Jako pole struktury, které obsahují řetězce podle hodnoty.|Vytvoří pole struktur, které obsahují řetězce a pole je předán podle hodnoty.|[Pole](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Viz také:
- [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)
- [Datové typy vyvolání platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))
- [Zařazování tříd, struktur a sjednocení](marshaling-classes-structures-and-unions.md)
- [Zařazování polí typů](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))
- [Různé ukázky zařazování](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))
