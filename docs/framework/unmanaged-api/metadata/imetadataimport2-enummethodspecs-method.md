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
ms.openlocfilehash: 8f6fbc570e7ea85aca5b365611d58a1700fb27cd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490715"
---
# <a name="imetadataimport2enummethodspecs-method"></a>IMetaDataImport2::EnumMethodSpecs – metoda
Získá enumerátor pro pole tokenů MethodSpec přidružených k zadanému tokenu MethodDef nebo MemberRef.  
  
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
 [in, out] Ukazatel na enumerátor pro `rMethodSpecs` .  
  
 `tk`  
 pro Token MemberRef nebo MethodDef, který představuje metodu, jejíž tokeny MethodSpec mají být vyčísleny. Pokud `tk` je hodnota 0 (nula), vyčíslení všech tokenů MethodSpec v oboru bude vyhodnoceno.  
  
 `rMethodSpecs`  
 mimo Pole tokenů MethodSpec k zobrazení výčtu.  
  
 `cMax`  
 pro Požadovaný maximální počet tokenů pro umístění `rMethodSpecs` .  
  
 `pcMethodSpecs`  
 mimo Vrácený počet tokenů, které jsou umístěny v `rMethodSpecs` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs`úspěšně vráceno.|  
|`S_FALSE`|`phEnum`neobsahuje žádné prvky členů. V tomto případě `pcMethodSpecs` je nastaveno na hodnotu 0 (nula).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
