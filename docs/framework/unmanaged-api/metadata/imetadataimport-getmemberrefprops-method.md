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
ms.openlocfilehash: 00693f1a87334620442e8865e76183b2dab68878
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503611"
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
 pro Požadovaná velikost v různých znacích `szMember` .  
  
 `pchMember`  
 mimo Vrácená velikost v různých znacích `szMember` .  
  
 `ppvSibBlob`  
 mimo Ukazatel na binární podpis metadat pro člena.  
  
 `pbSig`  
 mimo Velikost v bajtech `ppvSigBlob` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
