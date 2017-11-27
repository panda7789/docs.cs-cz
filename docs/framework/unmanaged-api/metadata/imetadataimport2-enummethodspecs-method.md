---
title: "IMetaDataImport2::EnumMethodSpecs – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumMethodSpecs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db1968c73d5a1c6e0687bc86f249c70b6c21712c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enummethodspecs-method"></a>IMetaDataImport2::EnumMethodSpecs – metoda
Získá enumerátor pro pole MethodSpec tokeny přidružený k zadané MethodDef nebo MemberRef token.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [ve out] Ukazatel na enumerátor pro `rMethodSpecs`.  
  
 `tk`  
 [v] MemberRef nebo MethodDef tokenu, který představuje metodu, jejichž MethodSpec tokeny mají být ve výčtu. Pokud hodnota `tk` je 0 (nula), bude možné provést výčet všech MethodSpec tokenů v oboru.  
  
 `rMethodSpecs`  
 [out] Pole MethodSpec tokenů pro zobrazení výčtu.  
  
 `cMax`  
 [v] Požadovaný maximální počet tokeny umístit `rMethodSpecs`.  
  
 `pcMethodSpecs`  
 [out] Vrácený počet tokeny umístěných v `rMethodSpecs`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs`úspěšně vrácena.|  
|`S_FALSE`|`phEnum`nemá žádné elementy člen. V takovém případě `pcMethodSpecs` je nastaven na hodnotu 0 (nula).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [Imetadataimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
