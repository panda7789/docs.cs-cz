---
ms.openlocfilehash: ab2907b05bff409fed9a370d5cbebbf3d1575d2f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235360"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>System.Threading.Tasks.Task již nezobrazují výjimku objectdisposedexception – po uvolnění objektu

|   |   |
|---|---|
|Podrobnosti|S výjimkou <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=name> metody již nezobrazují výjimku <xref:System.ObjectDisposedException?displayProperty=name> po vyřazení objektu. Tato změna podporuje používání úkolů v mezipaměti. Například metoda může vrátit úlohu uloženou v mezipaměti pro zastupování již dokončené operace namísto přidělení nové úlohy. To nebylo v předchozích verzích rozhraní .NET Framework možné, protože příjemci úlohy s ní mohli nakládat.|
|Doporučení|Mějte na paměti, že metody úloh může již nezobrazují výjimku <xref:System.ObjectDisposedException?displayProperty=name> v případech, kdy vyřazení objektu. Pokud aplikace se v závislosti na tuto výjimku vědět, že byl odstraněn úkolu, musí aktualizovat na hodnotu explicitně kontrolovat stav úlohy pomocí <xref:System.Threading.Tasks.Task.Status>.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
