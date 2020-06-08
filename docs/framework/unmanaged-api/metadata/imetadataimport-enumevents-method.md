---
title: IMetaDataImport::EnumEvents – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: 53b1234a176cade5876d70da0cb4eadc18802c69
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492301"
---
# <a name="imetadataimportenumevents-method"></a>IMetaDataImport::EnumEvents – metoda
Vytvoří výčet tokenů definice události pro zadaný token TypeDef.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] Ukazatel na enumerátor.  
  
 `td`  
 pro Token TypeDef, jehož definice událostí mají být vyčísleny.  
  
 `rEvents`  
 mimo Pole vrácených událostí  
  
 `cMax`  
 pro Maximální velikost `rEvents` pole.  
  
 `pcEvents`  
 mimo Skutečný počet událostí vrácených v `rEvents` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumEvents`úspěšně vráceno.|  
|`S_FALSE`|Nejsou k dispozici žádné události k zobrazení výčtu. V takovém případě `pcEvents` je nula.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
