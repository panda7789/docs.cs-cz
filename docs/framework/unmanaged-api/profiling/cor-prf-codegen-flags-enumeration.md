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
ms.openlocfilehash: 4dd4e39c9092d018f13e3bd2822e9492d71141ad
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867292"
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
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|Do těla této funkce nebudou vloženy žádné funkce. Samotná funkce však může být vložena do svých volajících.|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|Všechny optimalizace budou zakázány pro tělo této funkce. Samotná funkce však může být stále vložena do svých volajících.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_PRF_CODEGEN_FLAGS` výčet používá metoda [ICorProfilerFunctionControl:: SetCodegenFlags –](icorprofilerfunctioncontrol-setcodegenflags-method.md) , která umožňuje profileru řídit generování kódu pro funkci Rekompilované JIT.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](profiling-enumerations.md)
