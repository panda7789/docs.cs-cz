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
ms.openlocfilehash: 11ea6e468909ea42e38bdc7b76c60c460c98025e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503663"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField – metoda
Získá ukazatel na token FieldDef pro pole, které je ohraničené zadaným <xref:System.Type> a který má zadaný název a signaturu metadat.  
  
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
 pro Token TypeDef pro třídu nebo rozhraní, které obklopuje pole, které se má vyhledat. Pokud je tato hodnota `mdTokenNil` , vyhledávání je provedeno pro globální proměnnou.  
  
 `szName`  
 pro Název pole, které se má vyhledat  
  
 `pvSigBlob`  
 pro Ukazatel na binární podpis metadat pole.  
  
 `cbSigBlob`  
 pro Velikost v bajtech `pvSigBlob` .  
  
 `pmb`  
 mimo Ukazatel na odpovídajícího tokenu FieldDef.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte pole pomocí své nadřazené třídy nebo rozhraní () `td` , jeho název ( `szName` ) a volitelně jeho signatura ( `pvSigBlob` ).  
  
 Signatura předaná do `FindField` musí být vygenerována v aktuálním oboru, protože signatury jsou vázány na konkrétní obor. Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty. (Token je index do místní tabulky TypeDef). Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup do `FindField` .  
  
 `FindField`Vyhledá pouze pole, která byla definována přímo ve třídě nebo rozhraní; nenalezne zděděná pole.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
