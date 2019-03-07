---
title: IMetaDataImport::EnumSignatures – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de21f4bb91198a5eb77f94789d0389d97123b7a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472483"
---
# <a name="imetadataimportenumsignatures-method"></a>IMetaDataImport::EnumSignatures – metoda
Vytvoří výčet tokenů podpisu představující samostatné podpisy v aktuálním oboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out v] Ukazatel na enumerátor. První volání této metody musí mít hodnotu NULL.  
  
 `rSignatures`  
 [out] Pole pro ukládání tokenů podpisu.  
  
 `cMax`  
 [in] Maximální velikost `rSignatures` pole.  
  
 `pcSignatures`  
 [out] Počet tokenů podpisu pro vrácené v `rSignatures`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumSignatures` bylo úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné tokeny se vytvořit výčet. V takovém případě `pcSignatures` je nula.|  
  
## <a name="remarks"></a>Poznámky  
 Podpis tokeny jsou vytvářeny [imetadataemit::gettokenfromsig –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
