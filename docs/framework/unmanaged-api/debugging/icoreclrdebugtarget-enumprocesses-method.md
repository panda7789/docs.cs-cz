---
title: ICoreClrDebugTarget::EnumProcesses – metoda
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c09b70b5afb0561d32e55dd89df6cac083abc068
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses – metoda
Vytvoří výčet procesů, které běží na vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcProcs`  
 [out] Počet procesů, vrátí se v `ppProcs`. Tato hodnota může být 0 (nula).  
  
 `ppProcs`  
 [out] Pole [coreclrdebugprocinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) struktury, které představují procesů spuštěných na vzdáleném počítači.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěch.  
  
 E_OUTOFMEMORY  
 Nelze přidělit dostatek paměti pro `ppProcs`.  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 Jiné chyby.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li volné paměti, která byla přidělena touto metodou, volejte [icoreclrdebugtarget::freememory –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Knihovna:** mscordbi_macx86.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1  
  
## <a name="see-also"></a>Viz také  
 [ICoreClrDebugTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
