---
title: IMetaDataImport::EnumMembersWithName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
ms.openlocfilehash: ea451bdd645d2d4dea4c5dd00408e0bc51804803
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492067"
---
# <a name="imetadataimportenummemberswithname-method"></a>IMetaDataImport::EnumMembersWithName – metoda
Vytvoří výčet tokenů memberDef či představujících členy zadaného typu se zadaným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] Ukazatel na enumerátor.  
  
 `cl`  
 pro Token TypeDef představující typ s členy pro výčet.  
  
 `szName`  
 pro Název členu, který omezuje rozsah čítače.  
  
 `rMembers`  
 mimo Pole, které se používá k uložení tokenů memberDef či.  
  
 `cMax`  
 pro Maximální velikost `rMembers` pole.  
  
 `pcTokens`  
 mimo Skutečný počet memberDef či tokenů vrácených v `rMembers` .  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vytváří výčet polí a metod, ale ne vlastností nebo událostí. Na rozdíl od [IMetaDataImport:: enummembers –](imetadataimport-enummembers-method.md) `EnumMembersWithName` zahodí všechny tokeny Field a member, které nemají zadaný název.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`úspěšně vráceno.|  
|`S_FALSE`|Nejsou k dispozici žádné tokeny memberDef či pro zobrazení výčtu. V takovém případě `pcTokens` je nula.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
