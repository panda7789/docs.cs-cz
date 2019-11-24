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
ms.openlocfilehash: 6f8df824ed36b7793d5f07e5b5cf51f65f9c8e24
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432237"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken – metoda
Indicates that the specified metadata token will be processed.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [in] The metadata token to be processed.  
  
## <a name="remarks"></a>Poznámky  
 Typically, you want a token to be processed if it is in the metadata scope. The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IHostFilter – rozhraní](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
