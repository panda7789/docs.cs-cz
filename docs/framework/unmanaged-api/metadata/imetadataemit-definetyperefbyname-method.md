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
ms.openlocfilehash: f005ee9d3d9d4b8977cd6a1838fe46015e604df5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777468"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName – metoda
Získá token metadat pro typ, který je definován v zadaném rozsahu, který se nenachází v aktuálním oboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tkResolutionScope`  
 [in] Token určující rozlišovací obor. Platné jsou následující typy tokenů:  
  
- `mdModuleRef`, pokud je typ definován ve stejném sestavení, ve kterém je definována volající.  
  
- `mdAssemblyRef`, pokud je typ definovaný v jiném sestavení než ten, ve kterém je definována volající.  
  
- `mdTypeRef`, pokud je typ vnořeného typu.  
  
- `mdModule`, pokud je typ definován ve stejném modulu, ve kterém je definována volající.  
  
- Hodnota Null, pokud je typ definován globálně.  
  
 `szName`  
 [in] Název cílového typu v kódování Unicode.  
  
 `ptr`  
 [out] Ukazatel `mdTypeRef` token, který je přiřazen k typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
