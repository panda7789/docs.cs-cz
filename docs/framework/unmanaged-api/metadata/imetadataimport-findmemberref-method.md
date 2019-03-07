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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a58cba0ce4672a479cf5af9467d024a1b1562fc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474286"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef – metoda
Získá ukazatel na token MemberRef pro člena, který je odkaz uzavřen parametrem <xref:System.Type> a, který má zadaný název a metadata podpis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Token TypeRef pro třídu nebo rozhraní, který obklopuje odkaz na člena pro hledání. Pokud je tato hodnota `mdTokenNil`, vyhledávání se provádí pro globální proměnnou nebo odkaz na globální funkce.  
  
 `szName`  
 [in] Název člena odkazu pro vyhledávání.  
  
 `pvSigBlob`  
 [in] Ukazatel na binární metadat podpisu člena odkazu.  
  
 `cbSigBlob`  
 [in] Velikost v bajtech `pvSigBlob`.  
  
 `pmr`  
 [out] Ukazatel na odpovídající token MemberRef.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte členu pomocí jeho nadřazené třídu nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).  
  
 Podpis předán `FindMemberRef` musí byly vytvořeny v aktuálním oboru, protože podpisy jsou vázány na určitém rozsahu. Podpis můžete vložit token, který identifikuje nadřazeného class nebo hodnotového typu. Token je index do místní tabulky TypeDef. Nelze sestavit podpis za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro `FindMemberRef`.  
  
 `FindMemberRef` Vyhledá pouze odkazy na členy, které byly definovány přímo v dané třídy nebo rozhraní; Nelze najít odkazy zděděný člen.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
