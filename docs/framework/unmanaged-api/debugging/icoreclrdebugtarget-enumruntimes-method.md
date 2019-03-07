---
title: ICoreClrDebugTarget::EnumRuntimes – metoda
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9b434edc10a7c11d738bd3fc10402ef3f83d9dc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468264"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>ICoreClrDebugTarget::EnumRuntimes – metoda
Vytvoří výčet common language runtime (CLRs) v zadané proces, který běží na vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a>Parametry  
 `dwInternalProcessID`  
 [in] Interní proces ID procesu, pro kterou chcete vytvořit výčet modulů runtime. Bude jím `m_dwInternalID` od odpovídajících [coreclrdebugprocinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).  
  
 `pcRuntimes`  
 [out] Počet modulů runtime, které jsou vráceny v `ppRuntimes`. Tato hodnota může být 0 (nula).  
  
 `ppRuntimes`  
 [out] Pole [coreclrdebugruntimeinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) struktury, které představují modulů runtime načten v vzdálenému cílovému procesu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěch.  
  
 S_FALSE  
 `dwInternalProcessID` se neshoduje s jakýkoli proces, který běží na počítači, pravděpodobně protože proces byl ukončen. `pcRuntimes` a `ppRuntimes` bude mít hodnotu null.  
  
 E_OUTOFMEMORY  
 Nepovedlo se přidělit dostatek paměti pro `ppRuntimes`.  
  
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
