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
ms.openlocfilehash: fce4f3875fbdb110134d6b7f684eff40821f6bdd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503676"
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
 pro Token TypeDef pro třídu nebo rozhraní, který obklopuje člena, který se má vyhledat. Pokud je tato hodnota `mdTokenNil` , vyhledávání je provedeno pro globální proměnnou nebo globální funkci.  
  
 `szName`  
 pro Název hledaného člena.  
  
 `pvSigBlob`  
 pro Ukazatel na binární podpis metadat člena.  
  
 `cbSigBlob`  
 pro Velikost v bajtech `pvSigBlob` .  
  
 `pmb`  
 mimo Ukazatel na odpovídajícího tokenu memberDef či.  
  
## <a name="remarks"></a>Poznámky  
 Určíte člena pomocí své nadřazené třídy nebo rozhraní ( `td` ), jeho název ( `szName` ) a volitelně jeho signatura ( `pvSigBlob` ). Třída nebo rozhraní může obsahovat více členů se stejným názvem. V takovém případě předejte signaturu člena, aby našli jedinečnou shodu.  
  
 Signatura předaná do `FindMember` musí být vygenerována v aktuálním oboru, protože signatury jsou vázány na konkrétní obor. Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty. Token je index do místní tabulky TypeDef. Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít ho jako vstup pro vstup do `FindMember` .  
  
 `FindMember`Vyhledá pouze členy, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné členy.  
  
> [!NOTE]
> `FindMember`je pomocná metoda. Volá [IMetaDataImport:: FindMethod –](imetadataimport-findmethod-method.md);. Pokud toto volání nenajde shodu, `FindMember` pak zavolá [IMetaDataImport:: findfield –](imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
