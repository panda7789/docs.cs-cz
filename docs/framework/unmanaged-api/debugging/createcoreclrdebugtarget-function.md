---
title: "CreateCoreClrDebugTarget – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5b05cc6c84f2f891691613a485d35d008ef79e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget – funkce
Vytvoří připojení k proxy server ladicí program, který běží na vzdáleném počítači a vrátí [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objekt, který můžete použít k dotazování spuštěných procesů a načíst moduly runtime ve vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwAddress`  
 [v] IPv4 adresu vzdáleného cílový počítač.  
  
 `ppTarget`  
 [out] Ukazatel na ukazatel na [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objekt, který bude vytvořen.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Počet CLRs v procesu byla úspěšně zjistit a byly správně zadat odpovídající popisovač a cesta pole.  
  
 E_OUTOFMEMORY  
 Nelze přidělit dostatek paměti pro `ppTarget`.  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 Jiné chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Knihovna:** mscordbi_macx86.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
