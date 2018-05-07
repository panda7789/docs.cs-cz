---
title: IMetaDataImport::EnumTypeDefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53ed486a885514d02bf2be9c473e102c2c5f0e15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
|`S_OK`|`EnumTypeDefs` úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné tokenů pro zobrazení výčtu. V takovém případě `pcTypeDefs` je nulová.|  
  
## <a name="remarks"></a>Poznámky  
 TypeDef token představuje typu například třídy nebo rozhraní, stejně jako jakýkoli typ přidané prostřednictvím mechanismus rozšiřitelnosti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
