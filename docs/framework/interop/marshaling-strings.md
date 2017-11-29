---
title: "Zařazování řetězců"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
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
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 750f4e6852cd5aa52d03f884edcbfbf80ed5fab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-strings"></a>Zařazování řetězců
Vyvolání platformy parametrů řetězce kopie, převod je z formátu rozhraní .NET Framework (Unicode) na nespravované formát (ANSI), v případě potřeby. Protože jsou neměnné spravované řetězce, vyvolání platformy je zpět z nespravované paměti spravované paměti při nekopíruje funkce vrátí hodnotu.  
  
 V následující tabulce je uveden seznam možností zařazování pro řetězce, popisuje jejich využití a obsahuje odkaz na odpovídající ukázce rozhraní .NET Framework.  
  
|String|Popis|Ukázka|  
|------------|-----------------|------------|  
|Podle hodnoty.|Předá řetězce jako parametry.|[MsgBox –](../../../docs/framework/interop/msgbox-sample.md)|  
|Jako výsledek.|Vrátí řetězce z nespravovaného kódu.|[Řetězce](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|Odkazem.|Předá řetězce jako vstup/výstup parametry s využitím <xref:System.Text.StringBuilder>.|[Vyrovnávací paměti](http://msdn.microsoft.com/en-us/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|Ve struktuře hodnotou.|Předá řetězce ve struktuře, která je v parametru.|[Struktury](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|Ve struktuře odkazem **(char\*)**.|Předá řetězce ve struktuře, která je parametr v nebo na více systémů. Nespravované funkce očekává ukazatel na znak vyrovnávací paměť a velikost vyrovnávací paměti je členem strukturu.|[Řetězce](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|Ve struktuře odkazem **(char[])**.|Předá řetězce ve struktuře, která je parametr v nebo na více systémů. Nespravované funkce očekává, že vyrovnávací paměť embedded znak.|[Osinfo –](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|Ve třídě hodnotou **(char\*)**.|Předá řetězce do třídy (třídy je parametr v nebo na více systémů). Nespravované funkce očekává ukazatel na znak.|[OpenFileDlg](http://msdn.microsoft.com/en-us/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|Ve třídě hodnotou **(char[])**.|Předá řetězce do třídy (třídy je parametr v nebo na více systémů). Nespravované funkce očekává, že vyrovnávací paměť embedded znak.|[Osinfo –](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|Jako pole řetězců hodnotou.|Vytvoří pole řetězců, je předaná hodnota.|[Pole](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|Jako pole struktury, které obsahují hodnotu řetězce.|Vytvoří pole struktury, která obsahují řetězce a pole je předaná hodnota.|[Pole](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Viz také  
 [Zařazování dat s voláním platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [Datové typy vyvolání platformy](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [Zařazování tříd, struktur a sjednocení](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)  
 [Zařazování pole typů](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [Různé zařazování ukázky](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)
