---
title: IMetaDataImport::EnumMemberRefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a08577f15a6fab0e630d40032a23c273ee935faa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992326"
---
# <a name="imetadataimportenummemberrefs-method"></a>IMetaDataImport::EnumMemberRefs – metoda
Vytvoří výčet MemberRef tokeny představující členů zadaného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out v] Ukazatel na enumerátor.  
  
 `tkParent`  
 [in] Token TypeDef, Odkaz TypeRef, MethodDef nebo Odkaz ModuleRef pro typ, jejíž členové jsou pro provedení výčtu.  
  
 `rMemberRefs`  
 [out] Pole pro ukládání tokenů MemberRef.  
  
 `cMax`  
 [in] Maximální velikost `rMemberRefs` pole.  
  
 `pcTokens`  
 [out] Skutečný počet tokenů MemberRef vrácené v `rMemberRefs`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumMemberRefs` bylo úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné tokeny MemberRef se vytvořit výčet. V takovém případě `pcTokens` je na nulu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
