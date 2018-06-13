---
title: _CorDllMain – funkce
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d541f834e829305fa2b091c45d0dc8f387bb55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431666"
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
