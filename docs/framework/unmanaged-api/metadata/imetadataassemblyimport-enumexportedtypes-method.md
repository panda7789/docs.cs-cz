---
title: IMetaDataAssemblyImport::EnumExportedTypes – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: 45e2348b4726447548544d975e60b93e464fb402
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450340"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a>IMetaDataAssemblyImport::EnumExportedTypes – metoda
Vytvoří výčet exportovaných typů, na které odkazuje manifest sestavení v aktuálním oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] Ukazatel na enumerátor. Při prvním volání metody `EnumExportedTypes` musí být hodnota null.  
  
 `rExportedTypes`  
 mimo Výčet `mdExportedType` tokeny metadat  
  
 `cMax`  
 pro Maximální počet `mdExportedType` tokenů, které lze umístit do pole `rExportedTypes`.  
  
 `pcTokens`  
 mimo Počet tokenů `mdExportedType` vlastněných v `rExportedTypes`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumExportedTypes` byla úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné tokeny k vytvoření výčtu. V takovém případě je `pcTokens` nastavena na hodnotu nula.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
