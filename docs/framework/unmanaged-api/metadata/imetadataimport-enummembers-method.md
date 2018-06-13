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
ms.openlocfilehash: 46ee8c62861a62ac044f295f7da082756d87347b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447630"
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
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [ve out] Ukazatel na enumerátor.  
  
 `cl`  
 [v] TypeDef token představující typ, jejíž členové jsou výčet.  
  
 `rMembers`  
 [out] Pole používané pro udržení MemberDef tokenů.  
  
 `cMax`  
 [v] Maximální velikost `rMembers` pole.  
  
 `pcTokens`  
 [out] Skutečný počet MemberDef tokeny, vrátí se v `rMembers`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné MemberDef tokenů pro zobrazení výčtu. V takovém případě `pcTokens` je nulová.|  
  
## <a name="remarks"></a>Poznámky  
 Při vytváření výčtů kolekcí členů pro třídu, `EnumMembers` vrátí pouze členové definované přímo na třídu. I v případě, že třída poskytuje implementaci pro tyto zděděné členy nevrátí žádné členy, které třídy dědí. Výčet zděděné členy, volající musí explicitně provede řetězu dědičnosti. Všimněte si, že pravidla pro řetězu dědičnosti se mohou lišit v závislosti na jazyce nebo kompilátoru, která vygenerované původní metadata.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
