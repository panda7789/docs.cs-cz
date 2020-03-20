---
title: IMetaDataImport::EnumMembers – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: 20c7a90f27defa18a5ef311d1f3a549b81fc5c40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175483"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers – metoda
Vyjmenovává tokeny MemberDef představující členy zadaného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [dovnitř, ven] Ukazatel na čítač výčtu.  
  
 `cl`  
 [v] A TypeDef token představující typ, jehož členy mají být uvedeny.  
  
 `rMembers`  
 [out] Pole používané k uložení tokenů MemberDef.  
  
 `cMax`  
 [v] Maximální velikost `rMembers` pole.  
  
 `pcTokens`  
 [out] Skutečný počet tokenů MemberDef `rMembers`vrácených v .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers`úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné tokeny MemberDef pro výčet. V tom `pcTokens` případě je nula.|  
  
## <a name="remarks"></a>Poznámky  
 Při výčtu kolekce členů pro třídu vrátí `EnumMembers` pouze členy (pole a metody, ale **ne** vlastnosti nebo události) definované přímo na třídu. Nevrátí žádné členy, které zdědí třídy, i v případě, že třída poskytuje implementaci pro tyto zděděné členy. Chcete-li vytvořit výčet zděděných členů, volající musí explicitně chodit řetězce dědičnosti. Všimněte si, že pravidla pro řetězec dědičnosti se může lišit v závislosti na jazyku nebo kompilátoru, který vyzařoval původní metadata.

 Vlastnosti a události nejsou výčty . `EnumMembers` Chcete-li vytvořit výčet těchto, použijte [EnumProperties](imetadataimport-enumproperties-method.md) nebo [EnumEvents](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
