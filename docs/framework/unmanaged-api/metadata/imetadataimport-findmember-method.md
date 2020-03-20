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
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177286"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember – metoda
Získá ukazatel na MemberDef token pro pole nebo metodu, která je uzavřena zadané <xref:System.Type> a který má zadaný název a metadata podpis.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [v] TypeDef token pro třídu nebo rozhraní, které obklopuje člen hledat. Pokud je `mdTokenNil`tato hodnota , vyhledávání se provádí pro globální proměnné nebo globální funkce.  
  
 `szName`  
 [v] Jméno člena, který má být hledán.  
  
 `pvSigBlob`  
 [v] Ukazatel na podpis binárních metadat člena.  
  
 `cbSigBlob`  
 [v] Velikost v bajtů `pvSigBlob`.  
  
 `pmb`  
 [out] Ukazatel na odpovídající token MemberDef.  
  
## <a name="remarks"></a>Poznámky  
 Člen zadejte pomocí jeho ohraničující třídy nebo rozhraní (`td`), jeho názvu (`szName`) a volitelně jeho podpisu (`pvSigBlob`). Ve třídě nebo rozhraní může být více členů se stejným názvem. V takovém případě předavěte podpis člena a najděte jedinečnou shodu.  
  
 Předaný `FindMember` podpis musí být vygenerován v aktuálním oboru, protože podpisy jsou vázány na určitý obor. Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty. Token je index do místní tabulky TypeDef. Nelze vytvořit podpis za běhu mimo kontext aktuálního oboru a použít tento `FindMember`podpis jako vstup pro vstup do aplikace .  
  
 `FindMember`vyhledá pouze členy, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné členy.  
  
> [!NOTE]
> `FindMember`je pomocná metoda. Volá [iMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Pokud toto volání nenajde `FindMember` shodu, pak volá [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
