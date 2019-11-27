---
title: IMetaDataImport::FindField – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: 842d6c0deb90bc45cb59454fb30fcc3544d742f1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437948"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField – metoda
Získá ukazatel na FieldDef token pro pole, které je uzavřeno zadaným <xref:System.Type> a který má zadaný název a signaturu metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 pro Token TypeDef pro třídu nebo rozhraní, které obklopuje pole, které se má vyhledat. Pokud je tato hodnota `mdTokenNil`, je vyhledávání provedeno pro globální proměnnou.  
  
 `szName`  
 pro Název pole, které se má vyhledat  
  
 `pvSigBlob`  
 pro Ukazatel na binární podpis metadat pole.  
  
 `cbSigBlob`  
 pro Velikost v bajtech `pvSigBlob`.  
  
 `pmb`  
 mimo Ukazatel na odpovídajícího tokenu FieldDef.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte pole pomocí své nadřazené třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho signaturu (`pvSigBlob`).  
  
 Podpis předaný do `FindField` musí být vygenerován v aktuálním oboru, protože signatury jsou vázány na konkrétní obor. Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty. (Token je index do místní tabulky TypeDef). Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro `FindField`.  
  
 `FindField` najde pouze pole, která byla definována přímo ve třídě nebo rozhraní; nenalezne zděděná pole.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
