---
title: FunctionLeave – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80d82e26fe54c5422d1140bba84830879f0b5c2d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781276"
---
# <a name="functionleave-function"></a>FunctionLeave – funkce
Oznámí profileru, že funkce se chystá vrácení volajícímu.  
  
> [!NOTE]
>  `FunctionLeave` Funkce je zastaralé v rozhraní .NET Framework 2.0. Bude nadále fungovat, ale bude mít za následek snížení výkonu. Použití [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) namísto toho funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcID`  
 [in] Identifikátor funkce, která vrací.  
  
## <a name="remarks"></a>Poznámky  
 `FunctionLeave` Funkce je zpětné volání, je nutné implementovat. Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.  
  
 Prováděcí modul nelze uložit žádné registry před voláním této funkce.  
  
- Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.  
  
 Provádění `FunctionLeave` by neměla blokovat, protože způsobí zpoždění uvolnění paměti. Implementace by se neměly pokoušet uvolňování paměti, protože zásobník nemusí být ve stavu přívětivá kolekce uvolnění paměti. Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionLeave` vrátí.  
  
 Také `FunctionLeave` funkce nesmí volat do spravovaného kódu nebo v jakékoli příčina způsob přidělování spravované paměti.  
  
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
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
