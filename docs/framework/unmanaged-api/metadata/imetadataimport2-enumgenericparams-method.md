---
title: IMetaDataImport2::EnumGenericParams – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 55709e79cd8bdb36fe1e32ee8a699fccb1b1bbc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175301"
---
# <a name="imetadataimport2enumgenericparams-method"></a>IMetaDataImport2::EnumGenericParams – metoda
Získá čítač pro pole tokenů obecných parametrů přidružených k zadanému tokenu TypeDef nebo MethodDef.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [dovnitř, ven] Ukazatel na čítač výčtu.  
  
 `tk`  
 [v] Token TypeDef nebo MethodDef, jehož obecné parametry mají být uvedeny.  
  
 `rGenericParams`  
 [out] Pole obecných parametrů pro výčet.  
  
 `cMax`  
 [v] Požadovaný maximální počet tokenů, `rGenericParams`které mají být umístit v .  
  
 `pcGenericParams`  
 [out] Vrácený počet tokenů `rGenericParams`umístěných v .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParams`úspěšně vrácena.|  
|`S_FALSE`|`phEnum`nemá žádné členské prvky. V tomto `pcGenericParams` případě je nastavena na 0 (nula).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
