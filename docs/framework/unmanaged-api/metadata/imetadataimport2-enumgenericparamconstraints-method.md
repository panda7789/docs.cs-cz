---
title: IMetaDataImport2::EnumGenericParamConstraints – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f66b0145dbaece7292d2ccad169a97fbb10b6d11
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959572"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a>IMetaDataImport2::EnumGenericParamConstraints – metoda
Získá enumerátor pro celou řadu omezeních obecných parametrů, které jsou přidružené k obecný parametr reprezentována zadaného tokenu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out v] Ukazatel na enumerátor.  
  
 `tk`  
 [in]   Token, který představuje obecný parametr, jehož omezení jsou pro provedení výčtu.  
  
 `rGenericParamConstraints`  
 [out] Pole omezeních obecných parametrů k vytvoření výčtu.  
  
 `cMax`  
 [in]   Maximální požadovaný počet tokenů, které mají být umístěny `rGenericParamConstraints`.  
  
 `pcGenericParamConstraints`  
 [out] Ukazatel na počet tokenů umístěny do `rGenericParamConstraints`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` bylo úspěšně vráceno.|  
|`S_FALSE`|`phEnum` nemá žádné elementy člena. V takovém případě `pcGenericParameterConstraints` je nastavena na hodnotu 0 (nula).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
