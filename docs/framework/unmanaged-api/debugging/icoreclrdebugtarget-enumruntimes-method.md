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
ms.openlocfilehash: 4b55ac1d895bfecbe74be447bd06f4aa22b9d04f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790784"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>ICoreClrDebugTarget::EnumRuntimes – metoda
Vytvoří výčet modulu CLR (Common Language Runtime) (CLRs) v zadaném procesu, který je spuštěn ve vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a>Parametry  
 `dwInternalProcessID`  
 pro Interní ID procesu, pro který chcete vytvořit výčet modulů runtime. Tato akce bude `m_dwInternalID`a z odpovídajících [coreclrdebugprocinfo –](coreclrdebugprocinfo-structure.md).  
  
 `pcRuntimes`  
 mimo Počet běhu vrácených v `ppRuntimes`. Tato hodnota může být 0 (nula).  
  
 `ppRuntimes`  
 mimo Pole struktur [coreclrdebugruntimeinfo –](coreclrdebugruntimeinfo-structure.md) , které reprezentují moduly runtime načtené ve vzdáleném cílovém procesu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Nástup.  
  
 S_FALSE  
 `dwInternalProcessID` neodpovídá žádnému procesu, který je spuštěn v počítači, pravděpodobně proto, že proces byl ukončen. `pcRuntimes` a `ppRuntimes` budou mít hodnotu null.  
  
 E_OUTOFMEMORY  
 Nelze přidělit dostatek paměti pro `ppRuntimes`.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Další chyby.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte metodu [ICoreClrDebugTarget:: FreeMemory –](icoreclrdebugtarget-freememory-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Library:** mscordbi_macx86.dll  
  
 **Verze .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Viz také:

- [ICoreClrDebugTarget – rozhraní](icoreclrdebugtarget-interface.md)
