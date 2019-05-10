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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d05475f06a206dcb88d198c713767618453d742e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586901"
---
# <a name="functionenter3-function"></a>FunctionEnter3 – funkce
Oznámí profileru, že se ovládací prvek předán funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionOrRemappedID`  
 [in] Identifikátor funkce, do které se předá řízení.  
  
## <a name="remarks"></a>Poznámky  
 `FunctionEnter3` Funkce zpětného volání oznámí profileru jako funkce je volána, ale nemá podpora argument kontroly. Použití [icorprofilerinfo3::setenterleavefunctionhooks3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) k registraci vaši implementaci této funkce.  
  
 `FunctionEnter3` Funkce je zpětné volání, je nutné implementovat. Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.  
  
 Prováděcí modul nelze uložit žádné registry před voláním této funkce.  
  
- Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
