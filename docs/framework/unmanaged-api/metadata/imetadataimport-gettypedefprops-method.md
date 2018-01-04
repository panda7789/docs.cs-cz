---
title: "IMetaDataImport::GetTypeDefProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3e7f2c2fe602ef3464766b62ef12e8f83767bf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettypedefprops-method"></a>IMetaDataImport::GetTypeDefProps – metoda
Vrátí informace metadat pro <xref:System.Type> reprezentována zadaný token TypeDef.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [v] TypeDef token, který představuje typ vrátit metadata pro.  
  
 `szTypeDef`  
 [out] Vyrovnávací paměť, která obsahuje název typu.  
  
 `cchTypeDef`  
 [v] Velikost v široké znaky `szTypeDef`.  
  
 `pchTypeDef`  
 [out] Počet široké znaky, vrátí se v `szTypeDef`.  
  
 `pdwTypeDefFlags`  
 [out] Ukazatel na žádné příznaky, které upravit definici typu. Tato hodnota je bitová maska z [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) výčtu.  
  
 `ptkExtends`  
 [out] TypeDef nebo Odkaz TypeRef metadata token, který představuje základní typ požadovaného typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
