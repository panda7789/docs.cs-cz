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
ms.openlocfilehash: 14b5f2227991e38ba66889d7e966ab24e714294c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422579"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>ICoreClrDebugTarget::EnumRuntimes – metoda
Vytvoří výčet běžné moduly runtime jazyka (CLRs) v zadané procesu, který je spuštěn ve vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwInternalProcessID`  
 [v] Interní proces ID procesu, pro který chcete vytvořit výčet moduly runtime. Bude jím `m_dwInternalID` z odpovídající [coreclrdebugprocinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).  
  
 `pcRuntimes`  
 [out] Číslo, vrátí se v modulech runtime `ppRuntimes`. Tato hodnota může být 0 (nula).  
  
 `ppRuntimes`  
 [out] Pole [coreclrdebugruntimeinfo –](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) struktury, které představují modulech runtime načten do vzdáleného Cílový proces.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěch.  
  
 S_FALSE  
 `dwInternalProcessID` neodpovídá jakýkoli proces, který běží na počítači, pravděpodobně, protože proces byl ukončen. `pcRuntimes` a `ppRuntimes` bude mít hodnotu null.  
  
 E_OUTOFMEMORY  
 Nelze přidělit dostatek paměti pro `ppRuntimes`.  
  
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
