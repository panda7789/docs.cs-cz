---
title: IMetaDataImport2::EnumMethodSpecs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 2df53ba53c64e042abc54a1d2ac043d301acdde9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177177"
---
# <a name="imetadataimport2enummethodspecs-method"></a>IMetaDataImport2::EnumMethodSpecs – metoda
Získá čítač pro pole MethodSpec tokeny přidružené k zadané MethodDef nebo MemberRef token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [dovnitř, ven] Ukazatel na čítač `rMethodSpecs`výčtu pro .  
  
 `tk`  
 [v] Token MemberRef nebo MethodDef, který představuje metodu, jejíž tokeny MethodSpec mají být uvedeny ve výčtu. Pokud `tk` je hodnota 0 (nula), budou uvedeny všechny tokeny MethodSpec v oboru.  
  
 `rMethodSpecs`  
 [out] Pole MethodSpec tokeny výčet.  
  
 `cMax`  
 [v] Požadovaný maximální počet tokenů, `rMethodSpecs`které mají být umístit v .  
  
 `pcMethodSpecs`  
 [out] Vrácený počet tokenů `rMethodSpecs`umístěných v .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs`úspěšně vrácena.|  
|`S_FALSE`|`phEnum`nemá žádné členské prvky. V tomto `pcMethodSpecs` případě je nastavena na 0 (nula).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
