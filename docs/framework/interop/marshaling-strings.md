---
title: Zařazování řetězců
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
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
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: adcdf55f3e33a48c4fd10ea243bb0ce3497f522f
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="marshaling-strings"></a>Zařazování řetězců
Vyvolání platformy parametrů řetězce kopie, převod je z formátu rozhraní .NET Framework (Unicode) na nespravované formát (ANSI), v případě potřeby. Protože jsou neměnné spravované řetězce, vyvolání platformy je zpět z nespravované paměti spravované paměti při nekopíruje funkce vrátí hodnotu.  
  
 V následující tabulce je uveden seznam možností zařazování pro řetězce, popisuje jejich využití a obsahuje odkaz na odpovídající ukázce rozhraní .NET Framework.  
  
|String|Popis|Ukázka|  
|------------|-----------------|------------|  
|Podle hodnoty.|Předá řetězce jako parametry.|[MsgBox](msgbox-sample.md)|  
|Jako výsledek.|Vrátí řetězce z nespravovaného kódu.|[Řetězce](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Odkazem.|Předá řetězce jako vstup/výstup parametry s využitím <xref:System.Text.StringBuilder>.|[Vyrovnávací paměti](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100))|  
|Ve struktuře hodnotou.|Předá řetězce ve struktuře, která je v parametru.|[Struktury](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100))|  
|Ve struktuře odkazem **(char\*)**.|Předá řetězce ve struktuře, která je parametr v nebo na více systémů. Nespravované funkce očekává ukazatel na znak vyrovnávací paměť a velikost vyrovnávací paměti je členem strukturu.|[Řetězce](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Ve struktuře odkazem **(char[])**.|Předá řetězce ve struktuře, která je parametr v nebo na více systémů. Nespravované funkce očekává, že vyrovnávací paměť embedded znak.|[Osinfo –](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Ve třídě hodnotou **(char\*)**.|Předá řetězce do třídy (třídy je parametr v nebo na více systémů). Nespravované funkce očekává ukazatel na znak.|[OpenFileDlg](https://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75(v=vs.100))|  
|Ve třídě hodnotou **(char[])**.|Předá řetězce do třídy (třídy je parametr v nebo na více systémů). Nespravované funkce očekává, že vyrovnávací paměť embedded znak.|[Osinfo –](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Jako pole řetězců hodnotou.|Vytvoří pole řetězců, je předaná hodnota.|[Pole](marshaling-different-types-of-arrays.md)|  
|Jako pole struktury, které obsahují hodnotu řetězce.|Vytvoří pole struktury, která obsahují řetězce a pole je předaná hodnota.|[Pole](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Viz také  
 [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)  
 [Datové typy vyvolání platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Zařazování tříd, struktur a sjednocení](marshaling-classes-structures-and-unions.md)  
 [Zařazování pole typů](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))  
 [Různé zařazování ukázky](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))
