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
ms.openlocfilehash: 7410f91a853f3a677a105dc2e12a86d723c9fad6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177323"
---
# <a name="imetadataimportenummemberswithname-method"></a>IMetaDataImport::EnumMembersWithName – metoda
Výčet tokenů MemberDef představujících členy zadaného typu se zadaným názvem.  
  
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
 [dovnitř, ven] Ukazatel na čítač výčtu.  
  
 `cl`  
 [v] A TypeDef token představující typ s členy výčet.  
  
 `szName`  
 [v] Název člena, který omezuje rozsah čítače výčtu.  
  
 `rMembers`  
 [out] Pole používané k uložení tokenů MemberDef.  
  
 `cMax`  
 [v] Maximální velikost `rMembers` pole.  
  
 `pcTokens`  
 [out] Skutečný počet tokenů MemberDef `rMembers`vrácených v .  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vyjmenovává pole a metody, ale ne vlastnosti nebo události. Na rozdíl od [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` zahodí všechny tokeny polí a členů, které nemají zadaný název.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné tokeny MemberDef pro výčet. V tom `pcTokens` případě je nula.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
