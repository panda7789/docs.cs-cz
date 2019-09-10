---
title: FunctionTailcall – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12ec27277fe57bd1a291c2cfe491ea2c6f40c30e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851158"
---
# <a name="functiontailcall-function"></a>FunctionTailcall – funkce
Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce.  
  
> [!NOTE]
> `FunctionTailcall` Funkce je zastaralá ve verzi .NET Framework 2,0. Bude i nadále fungovat, ale dojde k snížení výkonu. Místo toho použijte funkci [FunctionTailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcID`  
 pro Identifikátor aktuálně vykonávané funkce, která má být volána pro volání funkce tail.  
  
## <a name="remarks"></a>Poznámky  
 Cílová funkce volání Tail bude používat aktuální rámec zásobníku a vrátí se přímo volajícímu funkce, která provedla volání funkce tail. To znamená, že zpětné volání [FunctionLeave –](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) nebude vystaveno pro funkci, která je cílem volání funkce tail.  
  
 `FunctionTailcall` Funkce je zpětné volání. je nutné ji implementovat. Implementace musí používat `__declspec`atribut třídy úložiště`naked`().  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
 Implementace `FunctionTailcall` by neměla blokovat, protože by se zpozdilo uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti. Při pokusu o uvolnění paměti modul runtime zablokuje, dokud `FunctionTailcall` se nevrátí.  
  
 `FunctionTailcall` Funkce také nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorProf.idl  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také:

- [FunctionEnter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
