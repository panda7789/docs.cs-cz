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
ms.openlocfilehash: acb772a64c8f13405f2836bb5f4f308986dce414
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447653"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers – metoda
Vytvoří výčet tokenů memberDef či představujících členy zadaného typu.  
  
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
 [in, out] Ukazatel na enumerátor.  
  
 `cl`  
 pro Token TypeDef představující typ, jehož členy mají být vyčísleny.  
  
 `rMembers`  
 mimo Pole použité pro ukládání tokenů memberDef či.  
  
 `cMax`  
 pro Maximální velikost `rMembers` pole  
  
 `pcTokens`  
 mimo Skutečný počet memberDef či tokenů vrácených v `rMembers`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` byla úspěšně vrácena.|  
|`S_FALSE`|Nejsou k dispozici žádné tokeny memberDef či pro zobrazení výčtu. V takovém případě je `pcTokens` nula.|  
  
## <a name="remarks"></a>Poznámky  
 Při vytváření výčtu kolekcí členů pro třídu `EnumMembers` vrátí pouze členy (pole a metody, ale **ne** vlastnosti nebo události) definované přímo na třídu. Nevrací žádné členy, které třída dědí, a to i v případě, že třída poskytuje implementaci pro tyto zděděné členy. Chcete-li vytvořit výčet zděděných členů, volající musí explicitně procházet řetěz dědičnosti. Všimněte si, že pravidla pro řetěz dědičnosti se mohou lišit v závislosti na jazyku nebo kompilátoru, který vyvolal původní metadata.
 
 Vlastnosti a události nejsou výčtem `EnumMembers`. K zobrazení výčtu použijte [enumproperties –](imetadataimport-enumproperties-method.md) nebo [enumevents –](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
