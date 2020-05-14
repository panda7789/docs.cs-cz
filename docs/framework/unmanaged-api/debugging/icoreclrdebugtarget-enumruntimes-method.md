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
ms.openlocfilehash: fc8269d4cc22ab53569edaa48c27b4a01970dcc7
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397178"
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
 pro Interní ID procesu, pro který chcete vytvořit výčet modulů runtime. To bude `m_dwInternalID` z odpovídající [coreclrdebugprocinfo –](coreclrdebugprocinfo-structure.md).  
  
 `pcRuntimes`  
 mimo Počet vrácených modulem runtime `ppRuntimes` . Tato hodnota může být 0 (nula).  
  
 `ppRuntimes`  
 mimo Pole struktur [coreclrdebugruntimeinfo –](coreclrdebugruntimeinfo-structure.md) , které reprezentují moduly runtime načtené ve vzdáleném cílovém procesu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěch.  
  
 S_FALSE  
 `dwInternalProcessID`neodpovídá žádnému procesu, který je spuštěn v počítači, pravděpodobně proto, že proces byl ukončen. `pcRuntimes`a `ppRuntimes` bude mít hodnotu null.  
  
 E_OUTOFMEMORY  
 Nelze přidělit dostatek paměti pro `ppRuntimes` .  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Další chyby.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte metodu [ICoreClrDebugTarget:: FreeMemory –](icoreclrdebugtarget-freememory-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Knihovna:** mscordbi_macx86. dll  
  
 **Verze .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Viz také

- [ICoreClrDebugTarget – rozhraní](icoreclrdebugtarget-interface.md)
