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
ms.openlocfilehash: 8541e7761e2f8e1839d028fdaea3eb71307ba615
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131203"
---
# <a name="_corexemain-function"></a>_CorExeMain – funkce
Inicializuje modul CLR (Common Language Runtime), vyhledá spravovaný vstupní bod v záhlaví modulu CLR spustitelného sestavení a zahájí provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je volána zavaděčem v procesech vytvořených ze spravovaných spustitelných sestavení. Pro sestavení knihoven DLL volá zavaděč funkci [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) .  
  
 Zavaděč operačního systému volá tuto metodu bez ohledu na vstupní bod zadaný v souboru obrázku.  
  
 V systémech Windows 98, Windows MILLENNIUM, Windows NT a Windows 2000 je funkce `_CorExeMain` volána nepřímo prostřednictvím opravy v zavaděči operačního systému. Ve všech ostatních verzích systému Windows je volána přímo zavaděčem operačního systému.  
  
 Další informace najdete v části poznámky v tématu [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
