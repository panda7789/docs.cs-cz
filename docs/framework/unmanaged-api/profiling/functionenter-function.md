---
title: FunctionEnter – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6018b5b06a138b38b7b97df280a3e4c4ea0512d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208407"
---
# <a name="functionenter-function"></a>FunctionEnter – funkce
Oznámí profileru, že se ovládací prvek předán funkci.  
  
> [!NOTE]
>  `FunctionEnter` Funkce je zastaralé v rozhraní .NET Framework verze 2.0 a jejich použití bude mít za následek snížení výkonu. Použití [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) namísto toho funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcID`  
 [in] Identifikátor funkce, do které se předá řízení.  
  
## <a name="remarks"></a>Poznámky  
 `FunctionEnter` Funkce je zpětné volání, je nutné implementovat. Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.  
  
 Prováděcí modul nelze uložit žádné registry před voláním této funkce.  
  
-   Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).  
  
-   Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.  
  
 Provádění `FunctionEnter` by neměla blokovat, protože způsobí zpoždění uvolnění paměti. Implementace by se neměly pokoušet uvolňování paměti, protože zásobník nemusí být ve stavu přívětivá kolekce uvolnění paměti. Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionEnter` vrátí.  
  
 Také `FunctionEnter` funkce nesmí volat do spravovaného kódu nebo v jakékoli příčina způsob přidělování spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také:

- [FunctionEnter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilace globálních statických funkcí](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
