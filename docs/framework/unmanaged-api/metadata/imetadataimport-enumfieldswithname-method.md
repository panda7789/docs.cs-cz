---
title: "IMetaDataImport::EnumFieldsWithName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumFieldsWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77b5ba7e191d9aa0f1587e4ac1ec25e655c27b14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumfieldswithname-method"></a>IMetaDataImport::EnumFieldsWithName – metoda
Vytvoří výčet FieldDef tokeny zadaného typu se zadaným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [ve out] Ukazatel na enumerátor.  
  
 `cl`  
 [v] Token typu, jehož pole jsou na vytvoření výčtu.  
  
 `szName`  
 [v] Název pole, která omezuje obor výčtu.  
  
 `rFields`  
 [out] Pole používá k ukládání FieldDef tokenů.  
  
 `cMax`  
 [v] Maximální velikost `rFields` pole.  
  
 `pcTokens`  
 [out] Skutečný počet FieldDef tokeny, vrátí se v `rFields`.  
  
## <a name="remarks"></a>Poznámky  
 Na rozdíl od [imetadataimport::enumfields –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` zahodí všechny tokeny pole, které nemají zadaný název.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumFieldsWithName`úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádná pole pro vytvoření výčtu. V takovém případě `pcTokens` je nulová.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
