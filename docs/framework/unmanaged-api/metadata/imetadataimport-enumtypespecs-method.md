---
title: IMetaDataImport::EnumTypeSpecs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 94b4c3935c949c0c4008e41244713b6bfa4dba84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503715"
---
# <a name="imetadataimportenumtypespecs-method"></a>IMetaDataImport::EnumTypeSpecs – metoda
Vytvoří výčet tokenů token TypeSpec definovaných v aktuálním oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] Ukazatel na enumerátor. Tato hodnota musí být pro první volání této metody NULL.  
  
 `rTypeSpecs`  
 mimo Pole, které se používá k uložení tokenů token TypeSpec.  
  
 `cMax`  
 pro Maximální velikost `rTypeSpecs` pole.  
  
 `pcTypeSpecs`  
 mimo Počet vrácených tokenů token TypeSpec `rTypeSpecs` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeSpecs`úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné tokeny k vytvoření výčtu. V takovém případě `pcTypeSpecs` je nula.|  
  
## <a name="remarks"></a>Poznámky  
 Tokeny token TypeSpec jsou vytvořeny metodou [IMetaDataEmit:: gettokenfromtypespec –](imetadataemit-gettokenfromtypespec-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
