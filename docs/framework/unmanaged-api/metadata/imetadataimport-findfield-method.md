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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88cd08b4290739808079bc8ecb713a5c5ea96584
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172559"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField – metoda
Získá ukazatel FieldDef token pro pole, který je uzavřen parametrem <xref:System.Type> a, který má zadaný název a metadata podpis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Token TypeDef pro třídu nebo rozhraní, který obklopuje pole pro hledání. Pokud je tato hodnota `mdTokenNil`, vyhledávání se provádí pro globální proměnné.  
  
 `szName`  
 [in] Název pole, které chcete vyhledat.  
  
 `pvSigBlob`  
 [in] Ukazatel na binární metadat podpis pole.  
  
 `cbSigBlob`  
 [in] Velikost v bajtech `pvSigBlob`.  
  
 `pmb`  
 [out] Ukazatel na odpovídající token FieldDef.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte pole pomocí jeho nadřazené třídu nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).  
  
 Podpis předán `FindField` musí byly vytvořeny v aktuálním oboru, protože podpisy jsou vázány na určitém rozsahu. Podpis můžete vložit token, který identifikuje nadřazeného class nebo hodnotového typu. (Token je index do místní tabulky TypeDef). Nelze sestavit podpis za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro `FindField`.  
  
 `FindField` Vyhledá pouze pole, které byly definovány přímo v dané třídy nebo rozhraní; Nelze najít zděděného pole.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
