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
ms.openlocfilehash: 6484832e8e737b9a0d0b3eaf3ede4078729f7a4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178442"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses – metoda
Vyjmenovává procesy spuštěné ve vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pcProcs`  
 [out] Počet vrácených procesů `ppProcs`v . Tato hodnota může být 0 (nula).  
  
 `ppProcs`  
 [out] Pole [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) struktury, které představují procesy spuštěné ve vzdáleném počítači.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěch  
  
 E_OUTOFMEMORY  
 Nelze přidělit dostatek `ppProcs`paměti pro .  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Další selhání.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li uvolnit paměť, která byla přidělena touto metodou, zavolejte metodu [ICoreClrDebugTarget::FreeMemory.](icoreclrdebugtarget-freememory-method.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Knihovna:** mscordbi_macx86.dll  
  
 **Verze rozhraní .NET Framework:** 3.5 SP1  
  
## <a name="see-also"></a>Viz také

- [ICoreClrDebugTarget – rozhraní](icoreclrdebugtarget-interface.md)
