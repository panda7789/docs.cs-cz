---
title: _CorExeMain – funkce
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63af5979b113f81c01c9c68d6cccdfa10811265a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429131"
---
# <a name="corexemain-function"></a>_CorExeMain – funkce
Inicializuje modul CLR (CLR), vyhledá spravované vstupní bod v záhlaví modulu CLR spustitelný soubor sestavení a zahájí spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je volána zavaděčem v procesů vytvořených ze spravovaných sestavení spustitelný soubor. Pro knihovny DLL sestavení zavaděč volá [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkce místo.  
  
 Zavaděč operačního systému volá tuto metodu, bez ohledu na to, vstupní bod uvedený v souboru bitové kopie.  
  
 V systému Windows 98, Windows ME, systém Windows NT a Windows 2000 `_CorExeMain` funkce je volána nepřímo prostřednictvím oprava zavaděče operačního systému. Ve všech ostatních verzí systému Windows je volána přímo zavaděčem operačního systému.  
  
 Další informace najdete v části poznámky v [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tématu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
