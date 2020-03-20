---
title: IMetaDataImport::FindMemberRef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175418"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef – metoda
Získá ukazatel na memberref token pro odkaz člena, který <xref:System.Type> je uzavřen zadaný a který má zadaný název a metadata podpisu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [v] TypeRef token pro třídu nebo rozhraní, které obklopuje odkaz na člena hledat. Pokud je `mdTokenNil`tato hodnota , vyhledávání se provádí pro globální proměnnou nebo odkaz na globální funkci.  
  
 `szName`  
 [v] Název členského odkazu pro hledání.  
  
 `pvSigBlob`  
 [v] Ukazatel na podpis binárních metadat členského odkazu.  
  
 `cbSigBlob`  
 [v] Velikost v bajtů `pvSigBlob`.  
  
 `pmr`  
 [out] Ukazatel na odpovídající MemberRef token.  
  
## <a name="remarks"></a>Poznámky  
 Člen zadejte pomocí jeho ohraničující třídy nebo rozhraní (`td`), jeho názvu (`szName`) a volitelně jeho podpisu (`pvSigBlob`).  
  
 Předaný `FindMemberRef` podpis musí být vygenerován v aktuálním oboru, protože podpisy jsou vázány na určitý obor. Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty. Token je index do místní tabulky TypeDef. Nelze vytvořit podpis za běhu mimo kontext aktuálního oboru a použít `FindMemberRef`tento podpis jako vstup do aplikace .  
  
 `FindMemberRef`vyhledá pouze členské odkazy, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné členské odkazy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
