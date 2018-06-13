---
title: IHostFilter::MarkToken – metoda
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52375486eb9d7780a51808dedc5f876587efb115
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444561"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken – metoda
Označuje, že zadaná metadata token budou zpracovány.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tk`  
 [v] Token metadata mají být zpracovány.  
  
## <a name="remarks"></a>Poznámky  
 Obvykle je vhodné token mají být zpracovány, pokud se nachází v oboru metadat. `MarkToken` Metodě se předává metadata stroji prostřednictvím [imetadataemit::sethandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IHostFilter – rozhraní](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
