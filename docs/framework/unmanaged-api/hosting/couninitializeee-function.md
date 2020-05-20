---
title: CoUninitializeEE – funkce
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: fa6297e926d53c02bb0d1af7b59b45b8ee152399
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616460"
---
# <a name="couninitializeee-function"></a>CoUninitializeEE – funkce
`CoUninitializeEE`je zastaralá a neposkytuje žádné funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 Modul pro spuštění společného jazykového modulu runtime nelze uvolnit z procesu. Pro vypnutí volání prováděcího modulu [CorExitProcess –](corexitprocess-function.md).  
  
## <a name="see-also"></a>Viz také

- [CoInitializeEE – funkce](coinitializeee-function.md)
- [Globální statické funkce pro metadata](../metadata/metadata-global-static-functions.md)
