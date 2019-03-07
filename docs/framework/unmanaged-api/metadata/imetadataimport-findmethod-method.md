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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 857ea06ad8aba2a6de87bdf670ad0462a2f7dde1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487279"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod – metoda
Získá ukazatel MethodDef token pro metodu, která je uzavřena parametrem <xref:System.Type> a, který má zadaný název a metadata podpis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] `mdTypeDef` Tokenů pro typ (třídu nebo rozhraní), který obklopuje členu, který chcete vyhledat. Pokud je tato hodnota `mdTokenNil`, pak vyhledávání se provádí pro globální funkce.  
  
 `szName`  
 [in] Název metody pro hledání.  
  
 `pvSigBlob`  
 [in] Ukazatel na binární metadat podpis metody.  
  
 `cbSigBlob`  
 [in] Velikost v bajtech `pvSigBlob`.  
  
 `pmb`  
 [out] Ukazatel na odpovídající token MethodDef.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte metodu, pomocí jeho nadřazené třídu nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`). Může existovat více metod se stejným názvem ve třídě nebo rozhraní. V takovém případě předejte podpis metody k vyhledání unikátní shoda.  
  
 Podpis předán `FindMethod` musí byly vytvořeny v aktuálním oboru, protože podpisy jsou vázány na určitém rozsahu. Podpis můžete vložit token, který identifikuje nadřazeného class nebo hodnotového typu. Token je index do místní tabulky TypeDef. Nelze sestavit podpis za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro vstup do `FindMethod`.  
  
 `FindMethod` Vyhledá pouze metody, které byly definovány přímo v dané třídy nebo rozhraní; Nelze najít zděděných metod.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
