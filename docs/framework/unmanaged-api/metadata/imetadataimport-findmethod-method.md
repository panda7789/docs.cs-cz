---
title: IMetaDataImport::FindMethod – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: c2ec907759a25048444ebcc81bf5bb0fd23ced58
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503650"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod – metoda
Získá ukazatel na token MethodDef pro metodu, která je ohraničena specifikovanou <xref:System.Type> a, která má zadaný název a signaturu metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 pro `mdTypeDef`Token pro typ (třída nebo rozhraní), který obklopuje člena k hledání. Pokud je tato hodnota `mdTokenNil` , pak se pro globální funkci provede vyhledávání.  
  
 `szName`  
 pro Název metody, která se má vyhledat.  
  
 `pvSigBlob`  
 pro Ukazatel na binární podpis metadat metody.  
  
 `cbSigBlob`  
 pro Velikost v bajtech `pvSigBlob` .  
  
 `pmb`  
 mimo Ukazatel na shodný token MethodDef.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte metodu pomocí své nadřazené třídy nebo rozhraní () `td` , jejího názvu ( `szName` ) a volitelně její signatura ( `pvSigBlob` ). V rámci třídy nebo rozhraní může existovat více metod se stejným názvem. V takovém případě předejte signaturu metody, abyste našli jedinečnou shodu.  
  
 Signatura předaná do `FindMethod` musí být vygenerována v aktuálním oboru, protože signatury jsou vázány na konkrétní obor. Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty. Token je index do místní tabulky TypeDef. Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít ho jako vstup pro vstup do `FindMethod` .  
  
 `FindMethod`najde pouze metody, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
