---
title: IMetaDataImport::GetMemberRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
ms.openlocfilehash: 1d6d66ea62cbf679f722f830b3638455001aedd6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437487"
---
# <a name="imetadataimportgetmemberrefprops-method"></a>IMetaDataImport::GetMemberRefProps – metoda
Načte metadata přidružená k členu, na který odkazuje zadaný token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mr`  
 pro Token MemberRef, pro který mají být vrácena přidružená metadata  
  
 `ptk`  
 mimo Token TypeDef nebo TypeRef nebo token token TypeSpec, který představuje třídu, která deklaruje člen, nebo token Odkaz ModuleRef, který reprezentuje třídu modulu, který deklaruje člen nebo prvek MethodDef, který představuje člena.  
  
 `szMember`  
 mimo Vyrovnávací paměť řetězce pro název člena.  
  
 `cchMember`  
 pro Požadovaná velikost v různých znacích `szMember`.  
  
 `pchMember`  
 mimo Vrácená velikost v různých znacích `szMember`.  
  
 `ppvSibBlob`  
 mimo Ukazatel na binární podpis metadat pro člena.  
  
 `pbSig`  
 mimo Velikost v bajtech `ppvSigBlob`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
