---
title: "IMetaDataImport::GetScopeProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetScopeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53e77a7bf0bd0aafc205469c4e101f8bfdcbe80b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetscopeprops-method"></a>IMetaDataImport::GetScopeProps – metoda
Získá název a volitelně identifikátor verze sestavení nebo modul v aktuálním oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [out] Vyrovnávací paměť pro název sestavení nebo modul.  
  
 `cchName`  
 [v] Velikost v široké znaky `szName`.  
  
 `pchName`  
 [out] Počet široké znaky, vrátí se v `szName`.  
  
 `pmvid`  
 [na víc systémů, volitelné] Ukazatel na identifikátor GUID, který jednoznačně identifikuje verzi sestavení nebo modul.  
  
## <a name="remarks"></a>Poznámky  
 [Imetadataemit::setmoduleprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) metoda se používá k nastavení těchto vlastností.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
