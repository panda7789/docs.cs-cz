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
ms.openlocfilehash: db3c3d38e0200f9849c84d7605a436816d56b813
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427422"
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
 `funcId`  
 pro Identifikátor aktuálně vykonávané funkce, která má být volána pro volání funkce tail.  
  
 `clientData`  
 pro Znovu namapovaný identifikátor funkce, který Profiler dříve zadal prostřednictvím [FunctionIDMapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)aktuálně vykonávané funkce, která se chystá udělat volání funkce tail.  
  
 `func`  
 pro Hodnota `COR_PRF_FRAME_INFO`, která odkazuje na informace o snímku zásobníku.  
  
 Profiler by měl považovat za neprůhledný popisovač, který lze předat zpět spouštěcímu modulu v metodě [ICorProfilerInfo2:: GetFunctionInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
## <a name="remarks"></a>Poznámky  
 Cílová funkce volání Tail bude používat aktuální rámec zásobníku a vrátí se přímo volajícímu funkce, která provedla volání funkce tail. To znamená, že zpětné volání [FunctionLeave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) nebude vystaveno pro funkci, která je cílem volání funkce tail.  
  
 Hodnota parametru `func` není po vrácení `FunctionTailcall2` funkce platná, protože hodnota se může změnit nebo zničit.  
  
 Funkce `FunctionTailcall2` je zpětné volání; je nutné jej implementovat. Implementace musí používat atribut třídy úložiště `__declspec`(`naked`).  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
 Implementace `FunctionTailcall2` by neměla zablokovat, protože bude odloženo uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti. V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionTailcall2` nevrátí.  
  
 Také funkce `FunctionTailcall2` nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [FunctionEnter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
