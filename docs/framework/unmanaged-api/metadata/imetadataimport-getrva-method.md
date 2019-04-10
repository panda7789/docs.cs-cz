---
title: IMetaDataImport::GetRVA – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96c013cd3e45e4ede0cbc9f42bf511a2eb3fc12d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223586"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA – metoda
Získá relativní virtuální adresu (RVA) a příznaky implementace metody nebo pole reprezentována zadaného tokenu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [in] MethodDef či FieldDef token metadat, který představuje objekt kódu se vraťte adresu RVA pro. Pokud je token FieldDef, pole musí být globální proměnné.  
  
 `pulCodeRVA`  
 [out] Ukazatel na relativní virtuální adresu kód objektu reprezentovaného parametrem tokenu.  
  
 `pdwImplFlags`  
 [out] Ukazatel na implementaci příznaky pro metodu. Tato hodnota je bitová maska z [cormethodimpl –](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčtu. Hodnota `pdwImplFlags` je platný pouze tehdy, pokud `tk` je MethodDef token.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
