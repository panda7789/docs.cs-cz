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
ms.openlocfilehash: 59512cc1c1b280d7fe6deb2f9d721ad53547e356
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437952"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef – metoda
Získá ukazatel na token MemberRef pro odkaz na člena, který je uzavřený zadaným <xref:System.Type> a který má zadaný název a signaturu metadat.  
  
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
 pro Token TypeRef pro třídu nebo rozhraní, které obklopují odkaz na člena pro hledání. Pokud je tato hodnota `mdTokenNil`, vyhledávání je provedeno pro globální proměnnou nebo odkaz globální funkce.  
  
 `szName`  
 pro Název odkazu na člena, který se má vyhledat  
  
 `pvSigBlob`  
 pro Ukazatel na binární podpis metadat odkazu na člena.  
  
 `cbSigBlob`  
 pro Velikost v bajtech `pvSigBlob`.  
  
 `pmr`  
 mimo Ukazatel na shodný token MemberRef.  
  
## <a name="remarks"></a>Poznámky  
 Určíte člena pomocí jeho nadřazené třídy nebo rozhraní (`td`), jeho názvu (`szName`) a volitelně jeho signatury (`pvSigBlob`).  
  
 Podpis předaný do `FindMemberRef` musí být vygenerován v aktuálním oboru, protože signatury jsou vázány na konkrétní obor. Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty. Token je index do místní tabulky TypeDef. Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro `FindMemberRef`.  
  
 `FindMemberRef` vyhledá pouze odkazy členů, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné odkazy členů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
