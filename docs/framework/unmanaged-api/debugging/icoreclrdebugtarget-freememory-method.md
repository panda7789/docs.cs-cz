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
ms.openlocfilehash: 061a2b9990d4b4d6398d0a31b97bc403a5f10de4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397160"
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
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Knihovna:** mscordbi_macx86. dll  
  
 **Verze .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Viz také

- [ICoreClrDebugTarget – rozhraní](icoreclrdebugtarget-interface.md)
