---
title: FunctionTailcall2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: cb7e21e0c6aad5ebb328ae5d1a993716f96e8d47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500569"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 – funkce
Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce a poskytuje informace o bloku zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[in] identifikátor aktuálně vykonávané funkce, která se chystá udělat volání funkce tail.

- `clientData`

  \[in] identifikátor přemapované funkce, který profil dřív zadal přes [FunctionIDMapper –](functionidmapper-function.md), aktuálně vykonávané funkce, která se chystá udělat volání funkce tail.
  
- `func`

  \[in] `COR_PRF_FRAME_INFO` hodnota, která odkazuje na informace o snímku zásobníku.

  Profiler by měl považovat za neprůhledný popisovač, který lze předat zpět spouštěcímu modulu v metodě [ICorProfilerInfo2:: GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) .

## <a name="remarks"></a>Poznámky  
 Cílová funkce volání Tail bude používat aktuální rámec zásobníku a vrátí se přímo volajícímu funkce, která provedla volání funkce tail. To znamená, že zpětné volání [FunctionLeave2 –](functionleave2-function.md) nebude vystaveno pro funkci, která je cílem volání funkce tail.  
  
 Hodnota `func` parametru není platná, pokud se `FunctionTailcall2` funkce vrátí, protože se může změnit nebo zničit hodnota.  
  
 `FunctionTailcall2`Funkce je zpětné volání. je nutné ji implementovat. Implementace musí používat `__declspec` `naked` atribut třídy úložiště ().  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
 Implementace `FunctionTailcall2` by neměla blokovat, protože by se zpozdilo uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti. Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionTailcall2` nevrátí.  
  
 `FunctionTailcall2`Funkce také nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [FunctionEnter2 – funkce](functionenter2-function.md)
- [FunctionLeave2 – funkce](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 – metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
