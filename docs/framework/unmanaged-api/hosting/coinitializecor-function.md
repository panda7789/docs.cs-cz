---
title: CoInitializeCor – funkce
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8642c165c29f9ca63535a0efbb9dbb58d4660a49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160391"
---
# <a name="coinitializecor-function"></a>CoInitializeCor – funkce
`CoInitializeCor` je zastaralý.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete inicializovat modul common language runtime, použijte buď [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Cor.h  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
