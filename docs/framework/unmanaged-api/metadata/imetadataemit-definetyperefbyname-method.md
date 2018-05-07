---
title: IMetaDataEmit::DefineTypeRefByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4fd6102b65137a06009428c1245b80c0d44924a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName – metoda
Získá token metadat pro typ, který je definován v zadaném oboru, který není v aktuálním oboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tkResolutionScope`  
 [v] Token zadání oboru rozlišení. Platné jsou následující typy tokenů:  
  
-   `mdModuleRef`, pokud typ je definovaná ve stejném sestavení, ve kterém je definovaný volající.  
  
-   `mdAssemblyRef`, pokud typ je definována v sestavení než ten, ve kterém je definovaný volající.  
  
-   `mdTypeRef`, pokud je typ vnořeného typu.  
  
-   `mdModule`, pokud typ je definovaná ve stejném modulu, ve kterém je definovaný volající.  
  
-   Hodnota Null, pokud typ je definována globálně.  
  
 `szName`  
 [v] Název cílového typu ve formátu Unicode.  
  
 `ptr`  
 [out] Ukazatel `mdTypeRef` token, který je přiřazen k typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
