---
title: COR_PRF_CODEGEN_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
ms.openlocfilehash: c2c7ae7a8930949c79b5e24e2da75f3b4649e7f6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500985"
---
# <a name="cor_prf_codegen_flags-enumeration"></a>COR_PRF_CODEGEN_FLAGS – výčet
Definuje příznaky generování kódu, které lze nastavit pomocí metody [ICorProfilerFunctionControl:: SetCodegenFlags –](icorprofilerfunctioncontrol-setcodegenflags-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|Do těla této funkce nebudou vloženy žádné funkce. Samotná funkce však může být vložena do svých volajících.|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|Všechny optimalizace budou zakázány pro tělo této funkce. Samotná funkce však může být stále vložena do svých volajících.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_PRF_CODEGEN_FLAGS`Výčet je používán metodou [ICorProfilerFunctionControl:: SetCodegenFlags –](icorprofilerfunctioncontrol-setcodegenflags-method.md) , která umožňuje profileru řídit generování kódu pro funkci Rekompilované JIT.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](profiling-enumerations.md)
