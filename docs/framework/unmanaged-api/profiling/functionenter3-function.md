---
title: FunctionEnter3 – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: b435e1a3504dd623421f977ffc48264f8b0dcb5a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500699"
---
# <a name="functionenter3-function"></a>FunctionEnter3 – funkce
Upozorňuje profileru, že řízení je předáno funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a>Parametry

- `functionOrRemappedID`

  \[in] identifikátor funkce, do které byl ovládací prvek předán.

## <a name="remarks"></a>Poznámky  
 `FunctionEnter3`Funkce zpětného volání upozorní Profiler jako volání funkcí, ale nepodporuje kontrolu argumentů. K registraci implementace této funkce použijte [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) .  
  
 `FunctionEnter3`Funkce je zpětné volání. je nutné ji implementovat. Implementace musí používat `__declspec(naked)` atribut třídy úložiště.  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Functionleave3 –](functionleave3-function.md)
- [Functiontailcall3 –](functiontailcall3-function.md)
- [Functionenter3withinfo –](functionenter3withinfo-function.md)
- [Functionleave3withinfo –](functionleave3withinfo-function.md)
- [Functiontailcall3withinfo –](functiontailcall3withinfo-function.md)
- [Setenterleavefunctionhooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [Setenterleavefunctionhooks3withinfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md)
- [Setfunctionidmapper2 –](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
