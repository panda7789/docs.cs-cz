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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbcf6c842e7eee55609a9ea2a25cda4360f8dc95
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739288"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget – funkce
Vytvoří připojení k proxy ladicího programu, který běží na vzdáleném počítači a vrátí [icoreclrdebugtarget –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objekt, který můžete použít k dotazování, spuštěné procesy a načtené moduly runtime na vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAddress`  
 [in] Adresa IPv4 vzdálené cílové počítače.  
  
 `ppTarget`  
 [out] Ukazatel na ukazatel [icoreclrdebugtarget –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objekt, který bude vytvořen.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěšně bylo zjištěno číslo CLRs v procesu a odpovídající popisovač a pole cesty byly správně vyplněné.  
  
 E_OUTOFMEMORY  
 Nepovedlo se přidělit dostatek paměti pro `ppTarget`.  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Jiné chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Library:** mscordbi_macx86.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
