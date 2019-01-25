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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 51eeaf79e470e38461450c6f4afbef982cca7a34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727960"
---
# <a name="imetadataimport2enumgenericparams-method"></a>IMetaDataImport2::EnumGenericParams – metoda
Získá enumerátor pro celou řadu obecný parametr tokeny přidružené k zadaným TypeDef nebo MethodDef token.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [out v] Ukazatel na enumerátor.  
  
 `tk`  
 [in] Token TypeDef nebo MethodDef jehož generické parametry jsou pro provedení výčtu.  
  
 `rGenericParams`  
 [out] Pole obecných parametrů k vytvoření výčtu.  
  
 `cMax`  
 [in] Maximální požadovaný počet tokenů, které mají být umístěny `rGenericParams`.  
  
 `pcGenericParams`  
 [out] Vrácený počet tokenů umístit v `rGenericParams`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParams` bylo úspěšně vráceno.|  
|`S_FALSE`|`phEnum` nemá žádné elementy člena. V takovém případě `pcGenericParams` je nastavena na hodnotu 0 (nula).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
