---
title: "IMetaDataImport::EnumTypeDefs – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeDefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a07d9ff237e6d3838fffb068e3a9ebf9febf66fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtypedefs-method"></a>IMetaDataImport::EnumTypeDefs – metoda
Vytvoří výčet TypeDef tokeny představující všechny typy v aktuálním oboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [out] Ukazatel na nové enumerátor. Toto musí mít hodnotu NULL pro první volání této metody.  
  
 `rTypeDefs`  
 [v] Pole používá k ukládání TypeDef tokenů.  
  
 `cMax`  
 [v] Maximální velikost `rTypeDefs` pole.  
  
 `pcTypeDefs`  
 [out] Počet TypeDef tokeny, vrátí se v `rTypeDefs`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné tokenů pro zobrazení výčtu. V takovém případě `pcTypeDefs` je nulová.|  
  
## <a name="remarks"></a>Poznámky  
 TypeDef token představuje typu například třídy nebo rozhraní, stejně jako jakýkoli typ přidané prostřednictvím mechanismus rozšiřitelnosti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Imetadataimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
