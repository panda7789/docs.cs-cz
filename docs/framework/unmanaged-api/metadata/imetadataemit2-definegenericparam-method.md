---
title: "IMetaDataEmit2::DefineGenericParam – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.DefineGenericParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 598c616ca91b73d9cb184d9e431e75d00d3f9850
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2definegenericparam-method"></a>IMetaDataEmit2::DefineGenericParam – metoda
Vytvoří definici pro parametr obecného typu a získá token pro tento parametr obecného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tk`  
 [v] `mdTypeDef` Nebo `mdMethodDef` token, který představuje metoda nebo konstruktor, pro které chcete definovat obecný parametr.  
  
 `ulParamSeq`  
 [v] Index obecný parametr.  
  
 `dwParamFlags`  
 [v] Hodnota [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) výčet, který popisuje typ pro obecný parametr.  
  
 `szname`  
 [v] Název parametru.  
  
 `reserved`  
 [v] Tento parametr je vyhrazená pro budoucí rozšíření.  
  
 `rtkConstraints`  
 [v] Byl ukončen nula pole Typ omezení. Pole členů musí být `mdTypeDef`, `mdTypeRef`, nebo `mdTypeSpec` metadata token.  
  
 `pgp`  
 [out] Token, který reprezentuje obecný parametr.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
