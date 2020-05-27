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
ms.openlocfilehash: 11529ce896f265f2b200fa6e511d4b913e9147c8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008219"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken – metoda
Indikuje, že se zpracuje zadaný token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 pro Token metadat, který má být zpracován.  
  
## <a name="remarks"></a>Poznámky  
 Obvykle chcete zpracovat token, pokud je v oboru metadat. `MarkToken`Metoda je předána modulu metadat pomocí metody [IMetaDataEmit:: SetHandler –](imetadataemit-sethandler-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro metadata](metadata-interfaces.md)
- [IHostFilter – rozhraní](ihostfilter-interface.md)
