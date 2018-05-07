---
title: Init – metoda
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b512389078ab022208c4b163edc8501a900669ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="init-method"></a>Init – metoda
Připraví objekty implementace [ialink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) pro použití.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDispenser`  
 [Imetadatadispenserex – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) ukazatel na enumenátor metadat.  
  
 `pErrorHandler`  
 [Imetadataerror – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) ukazatel na volitelné rozhraní pro zpracování chyby.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h  
  
## <a name="see-also"></a>Viz také  
 [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
