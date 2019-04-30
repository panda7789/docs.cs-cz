---
title: IMetaDataImport::FindMember – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63afd82ca88e1a7c61913ec7fcc4d77d03ae9927
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777927"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember – metoda
Získá ukazatel MemberDef token pro pole nebo metoda, která je uzavřena parametrem <xref:System.Type> a, který má zadaný název a metadata podpis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [in] Token TypeDef pro třídu nebo rozhraní, který obklopuje členu, který chcete vyhledat. Pokud je tato hodnota `mdTokenNil`, vyhledávání se provádí pro globální proměnnou nebo globální funkce.  
  
 `szName`  
 [in] Název členu, který chcete vyhledat.  
  
 `pvSigBlob`  
 [in] Ukazatel na binární metadat podpisu člena.  
  
 `cbSigBlob`  
 [in] Velikost v bajtech `pvSigBlob`.  
  
 `pmb`  
 [out] Ukazatel na odpovídající MemberDef token.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte členu pomocí jeho nadřazené třídu nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`). Může existovat více členů se stejným názvem ve třídě nebo rozhraní. V takovém případě předejte podpis členu zobrazíte unikátní shoda.  
  
 Podpis předán `FindMember` musí byly vytvořeny v aktuálním oboru, protože podpisy jsou vázány na určitém rozsahu. Podpis můžete vložit token, který identifikuje nadřazeného class nebo hodnotového typu. Token je index do místní tabulky TypeDef. Nelze sestavit podpis za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro vstup do `FindMember`.  
  
 `FindMember` Vyhledá pouze členy, které byly definovány přímo v dané třídy nebo rozhraní; Nelze najít zděděných členů.  
  
> [!NOTE]
>  `FindMember` je pomocná metoda. Volá [imetadataimport::findmethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Pokud je toto volání nenajde shoda, `FindMember` pak zavolá [imetadataimport::findfield –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
