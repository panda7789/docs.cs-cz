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
ms.openlocfilehash: 4eefb7ec1e7d0d130ec64531a59d1d5bbce04963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968922"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember – metoda
Získá ukazatel na token memberDef či pole nebo metody, které jsou uzavřeny zadaným <xref:System.Type> a mají zadaný název a signaturu metadat.  
  
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
 pro Token TypeDef pro třídu nebo rozhraní, který obklopuje člena, který se má vyhledat. Pokud je `mdTokenNil`tato hodnota, vyhledávání je provedeno pro globální proměnnou nebo globální funkci.  
  
 `szName`  
 pro Název hledaného člena.  
  
 `pvSigBlob`  
 pro Ukazatel na binární podpis metadat člena.  
  
 `cbSigBlob`  
 pro Velikost v bajtech `pvSigBlob`.  
  
 `pmb`  
 mimo Ukazatel na odpovídajícího tokenu memberDef či.  
  
## <a name="remarks"></a>Poznámky  
 Určíte člena pomocí své nadřazené třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho signatura (`pvSigBlob`). Třída nebo rozhraní může obsahovat více členů se stejným názvem. V takovém případě předejte signaturu člena, aby našli jedinečnou shodu.  
  
 Signatura předaná `FindMember` do musí být vygenerována v aktuálním oboru, protože signatury jsou vázány na konkrétní obor. Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty. Token je index do místní tabulky TypeDef. Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít ho jako vstup pro vstup do `FindMember`.  
  
 `FindMember`Vyhledá pouze členy, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné členy.  
  
> [!NOTE]
> `FindMember`je pomocná metoda. Volá [IMetaDataImport:: FindMethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md);. Pokud toto volání nenajde shodu, `FindMember` pak zavolá [IMetaDataImport:: findfield –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** Cor. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
