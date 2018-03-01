---
title: "_CorDllMain – funkce"
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
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 985f2284026054217671de767c316b1fba35c098
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordllmain-function"></a>_CorDllMain – funkce
Inicializuje modul CLR (CLR), vyhledá spravované vstupní bod v záhlaví modulu CLR sestavení knihoven DLL a zahájí spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hInst`  
 [v] Instance popisovače načíst modul.  
  
 `dwReason`  
 [v] Označuje, proč je volána funkce vstupního bodu knihovny DLL. Tento parametr může být jedna z následujících hodnot: DLL_PROCESS_ATTACH DLL_THREAD_ATTACH, DLL_THREAD_ATTACH nebo DLL_PROCESS_DETACH. Popis těchto hodnot najdete v tématu `DllMain` dokumentace v sadě SDK pro platformu.  
  
 `lpReserved`  
 [v] Nepoužívá se.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí hodnotu `true` úspěch a `false` Pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je volána zavaděčem operačního systému pro knihovnu DLL sestavení. Pro spustitelný soubor sestavení zavaděč volá [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) funkce místo.  
  
 Zavaděč operačního systému volá tuto metodu, bez ohledu na to, vstupní bod uvedený v souboru DLL.  
  
 V systému Windows 98, Windows ME, systém Windows NT a Windows 2000 `_CorDllMain` je volána funkce nepřímo prostřednictvím fixupin zavaděč operačního systému. Ve všech ostatních verzí systému Windows je volána přímo zavaděčem operačního systému.  
  
 Další informace najdete v části poznámky v [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tématu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
