---
title: IMetaDataImport::EnumCustomAttributes – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 61b5678a546bdbadbcc6d8ee86447cb17ce72b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175522"
---
# <a name="imetadataimportenumcustomattributes-method"></a>IMetaDataImport::EnumCustomAttributes – metoda
Vyjmenovává tokeny vlastní definice atributu přidružené k zadanému typu nebo členu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [dovnitř, ven] Ukazatel na vrácený čítač výčtu.  
  
 `tk`  
 [v] Token pro rozsah výčtu nebo nula pro všechny vlastní atributy.  
  
 `tkType`  
 [v] Token pro konstruktor typu atributů, které mají být uvedeny `null` ve výčtu, nebo pro všechny typy.  
  
 `rCustomAttributes`  
 [out] Pole tokenů vlastních atributů.  
  
 `cMax`  
 [v] Maximální velikost `rCustomAttributes` pole.  
  
 `pcCustomAttributes`  
 [ven, nepovinné] Skutečný počet hodnot tokenu `rCustomAttributes`vrácených v .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes`úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné vlastní atributy výčet. V tom `pcCustomAttributes` případě je nula.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
