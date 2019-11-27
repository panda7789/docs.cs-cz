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
ms.openlocfilehash: 470b6511366cef1680eaf97f9ab376736add55c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437893"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod – metoda
Získá ukazatel na token MethodDef pro metodu, která je uzavřena zadaným <xref:System.Type> a která má zadaný název a signaturu metadat.  
  
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
 pro Token `mdTypeDef` pro typ (třída nebo rozhraní), který je členem pro hledání. Pokud je tato hodnota `mdTokenNil`, je vyhledávání provedeno pro globální funkci.  
  
 `szName`  
 pro Název metody, která se má vyhledat.  
  
 `pvSigBlob`  
 pro Ukazatel na binární podpis metadat metody.  
  
 `cbSigBlob`  
 pro Velikost v bajtech `pvSigBlob`.  
  
 `pmb`  
 mimo Ukazatel na shodný token MethodDef.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte metodu pomocí své nadřazené třídy nebo rozhraní (`td`), jejího názvu (`szName`) a volitelně její signaturu (`pvSigBlob`). V rámci třídy nebo rozhraní může existovat více metod se stejným názvem. V takovém případě předejte signaturu metody, abyste našli jedinečnou shodu.  
  
 Podpis předaný do `FindMethod` musí být vygenerován v aktuálním oboru, protože signatury jsou vázány na konkrétní obor. Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty. Token je index do místní tabulky TypeDef. Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup do `FindMethod`.  
  
 `FindMethod` najde pouze metody, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
