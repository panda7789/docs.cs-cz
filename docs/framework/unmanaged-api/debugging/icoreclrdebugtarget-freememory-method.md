---
title: ICoreClrDebugTarget::FreeMemory – metoda
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
ms.openlocfilehash: cfa313d286d0decad82f51bcedc582470549c8e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790777"
---
# <a name="icoreclrdebugtargetfreememory-method"></a>ICoreClrDebugTarget::FreeMemory – metoda
Uvolňuje paměť přidělená metodami [ICoreClrDebugTarget:: EnumProcesses –](icoreclrdebugtarget-enumprocesses-method.md) a [ICoreClrDebugTarget:: enumruntimes –](icoreclrdebugtarget-enumruntimes-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a>Parametry  
 `pMemory`  
 pro Ukazatel na pole, které je vráceno metodou [ICoreClrDebugTarget:: EnumProcesses –](icoreclrdebugtarget-enumprocesses-method.md) nebo [ICoreClrDebugTarget:: enumruntimes –](icoreclrdebugtarget-enumruntimes-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Library:** mscordbi_macx86.dll  
  
 **Verze .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Viz také:

- [ICoreClrDebugTarget – rozhraní](icoreclrdebugtarget-interface.md)
