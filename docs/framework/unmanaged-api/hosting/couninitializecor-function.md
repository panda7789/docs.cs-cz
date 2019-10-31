---
title: CoUninitializeCor – funkce
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
ms.openlocfilehash: eddc2f29da0efd9e56df710203b1d7621ffc27a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136868"
---
# <a name="couninitializecor-function"></a>CoUninitializeCor – funkce
`CoUninitializeCor` je zastaralá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (Common Language Runtime) nelze uvolnit z procesu. Chcete-li modul runtime zcela odebrat ze spuštěného procesu, je nutné tento proces vypnout.  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
