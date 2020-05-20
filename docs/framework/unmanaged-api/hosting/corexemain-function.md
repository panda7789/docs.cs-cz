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
ms.openlocfilehash: 935ac478fb966315e81fdcc004761038b28e3178
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616587"
---
# <a name="_corexemain-function"></a>_CorExeMain – funkce
Inicializuje modul CLR (Common Language Runtime), vyhledá spravovaný vstupní bod v záhlaví modulu CLR spustitelného sestavení a zahájí provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je volána zavaděčem v procesech vytvořených ze spravovaných spustitelných sestavení. Pro sestavení knihovny DLL volá zavaděč místo toho funkci [_CorDllMain](cordllmain-function.md) .  
  
 Zavaděč operačního systému volá tuto metodu bez ohledu na vstupní bod zadaný v souboru obrázku.  
  
 V systémech Windows 98, Windows MILLENNIUM, Windows NT a Windows 2000 `_CorExeMain` je funkce volána nepřímo prostřednictvím opravy v zavaděči operačního systému. Ve všech ostatních verzích systému Windows je volána přímo zavaděčem operačního systému.  
  
 Další informace najdete v části poznámky v tématu [_CorValidateImage](corvalidateimage-function.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Globální statické funkce pro metadata](../metadata/metadata-global-static-functions.md)
