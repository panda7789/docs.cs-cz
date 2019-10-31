---
title: CreateCoreClrDebugTarget – funkce
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: d52757f82a950c382c7c8f2162630eda7d7795e7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132096"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget – funkce
Vytvoří připojení k proxy serveru ladicího programu, který běží na vzdáleném počítači, a vrátí objekt [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) , který lze použít k dotazování na spuštěné procesy a načtených modulech runtime na vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAddress`  
 pro Adresa IPv4 vzdáleného cílového počítače.  
  
 `ppTarget`  
 mimo Ukazatel na ukazatel na objekt [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) , který se vytvoří.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Počet CLRs v procesu byl úspěšně zjištěn a odpovídající pole popisovače a cesty byly správně vyplněny.  
  
 E_OUTOFMEMORY  
 Nelze přidělit dostatek paměti pro `ppTarget`.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Další chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Knihovna:** mscordbi_macx86. dll  
  
 **Verze .NET Framework:** 3,5 SP1
