---
title: IMetaDataImport::EnumFieldsWithName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71a2c7a61d573c1e17d0e8fefcd34d60e05ed3c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780473"
---
# <a name="imetadataimportenumfieldswithname-method"></a>IMetaDataImport::EnumFieldsWithName – metoda
Vytvoří výčet FieldDef tokeny zadaného typu se zadaným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out v] Ukazatel na enumerátor.  
  
 `cl`  
 [in] Token typu, jehož pole jsou pro provedení výčtu.  
  
 `szName`  
 [in] Název pole, která omezuje rozsah výčtu.  
  
 `rFields`  
 [out] Pole pro ukládání tokenů FieldDef.  
  
 `cMax`  
 [in] Maximální velikost `rFields` pole.  
  
 `pcTokens`  
 [out] Skutečný počet tokenů FieldDef vrácené v `rFields`.  
  
## <a name="remarks"></a>Poznámky  
 Na rozdíl od [imetadataimport::enumfields –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` zahodí všechny tokeny pole, které nemají se zadaným názvem.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumFieldsWithName` bylo úspěšně vráceno.|  
|`S_FALSE`|Nejsou žádná pole pro zobrazení výčtu. V takovém případě `pcTokens` je nula.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
