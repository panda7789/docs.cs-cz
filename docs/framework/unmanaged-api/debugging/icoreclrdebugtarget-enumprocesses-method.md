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
ms.openlocfilehash: 8a35f5ff62ca37337b7becb023f2328cbe05aea6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216038"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses – metoda
Vytváří výčet procesů, které běží na vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pcProcs`  
 [out] Počet procesů, které jsou vráceny v `ppProcs`. Tato hodnota může být 0 (nula).  
  
 `ppProcs`  
 [out] Pole [coreclrdebugprocinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) struktury, které představují procesy spuštěné ve vzdáleném počítači.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěch.  
  
 E_OUTOFMEMORY  
 Nepovedlo se přidělit dostatek paměti pro `ppProcs`.  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Jiné chyby.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte [icoreclrdebugtarget::freememory –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Library:** mscordbi_macx86.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1  
  
## <a name="see-also"></a>Viz také:

- [ICoreClrDebugTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
