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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0845c4d493cb3c750931a0ae2ad92b628a255c0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202713"
---
# <a name="couninitializecor-function"></a>CoUninitializeCor – funkce
`CoUninitializeCor` je zastaralý.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a>Poznámky  
 Modul common language runtime nemůže být uvolněna z procesu. Modul runtime úplně odebrat ze spuštěného procesu, je nutné vypnout tohoto procesu.  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
