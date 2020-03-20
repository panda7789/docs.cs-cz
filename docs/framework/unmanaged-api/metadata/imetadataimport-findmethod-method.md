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
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177254"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod – metoda
Získá ukazatel na MethodDef token pro metodu, která <xref:System.Type> je uzavřena zadaný a který má zadaný název a metadata podpisu.  
  
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
 [v] Token `mdTypeDef` pro typ (třída nebo rozhraní), který obklopuje člena hledat. Pokud je `mdTokenNil`tato hodnota , pak vyhledávání se provádí pro globální funkce.  
  
 `szName`  
 [v] Název metody, kterou chcete vyhledat.  
  
 `pvSigBlob`  
 [v] Ukazatel na podpis binárních metadat metody.  
  
 `cbSigBlob`  
 [v] Velikost v bajtů `pvSigBlob`.  
  
 `pmb`  
 [out] Ukazatel na odpovídající token MethodDef.  
  
## <a name="remarks"></a>Poznámky  
 Metodu určíte pomocí její ohraničující třídy nebo rozhraní (`td`), její název (`szName`) a volitelně její podpis (`pvSigBlob`). Ve třídě nebo rozhraní může existovat více metod se stejným názvem. V takovém případě předavěte podpis metody a najděte jedinečnou shodu.  
  
 Předaný `FindMethod` podpis musí být vygenerován v aktuálním oboru, protože podpisy jsou vázány na určitý obor. Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty. Token je index do místní tabulky TypeDef. Nelze vytvořit podpis za běhu mimo kontext aktuálního oboru a použít tento `FindMethod`podpis jako vstup pro vstup do aplikace .  
  
 `FindMethod`vyhledá pouze metody, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
