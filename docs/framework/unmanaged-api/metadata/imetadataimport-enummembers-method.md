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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de4bf2cf647682062fbacb4484ffae905d1b7995
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835366"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers – metoda
Vytvoří výčet MemberDef tokeny představující členů zadaného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [out v] Ukazatel na enumerátor.  
  
 `cl`  
 [in] Token TypeDef představující typ, jejíž členové jsou pro provedení výčtu.  
  
 `rMembers`  
 [out] Pole sloužící k uchování MemberDef tokeny.  
  
 `cMax`  
 [in] Maximální velikost `rMembers` pole.  
  
 `pcTokens`  
 [out] Skutečný počet tokenů MemberDef vrácené v `rMembers`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` bylo úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné tokeny MemberDef výčet. V takovém případě `pcTokens` je nula.|  
  
## <a name="remarks"></a>Poznámky  
 Při vytváření výčtů kolekcí členů v případě třídy `EnumMembers` vrací pouze členy (polím a metodám, ale **není** vlastnosti nebo události) definované přímo ve třídě. I v případě, že třída poskytuje implementaci pro členy zděděné nevrací žádné členy, které dědí třídu. Výčet zděděné členy, volající musí explicitně provedou řetězu dědičnosti. Všimněte si, že pravidla pro řetězec dědičnosti mohou lišit v závislosti na jazyk nebo kompilátor, který původní metadata, protože ho.
 
 Vlastnosti a události, které nejsou ve výčtu `EnumMembers`. Chcete-li vytvořit výčet ty, použijte [enumproperties –](imetadataimport-enumproperties-method.md) nebo [enumevents –](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
