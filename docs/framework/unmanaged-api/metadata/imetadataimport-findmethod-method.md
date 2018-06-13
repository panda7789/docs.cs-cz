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
ms.openlocfilehash: 6b68d4e3d51fdb50290319de804a78c1a78a07a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447385"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod – metoda
Získá ukazatel na MethodDef token pro metodu, která je uzavřena k zadanému <xref:System.Type> a má zadaný název a metadata podpis.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [v] `mdTypeDef` Tokenu pro typ (třídy nebo rozhraní), která obklopuje člena pro vyhledávání. Pokud je tato hodnota `mdTokenNil`, pak se provádí vyhledávání pro globální funkce.  
  
 `szName`  
 [v] Název metody, které chcete vyhledat.  
  
 `pvSigBlob`  
 [v] Ukazatel na binární metadata podpis metody.  
  
 `cbSigBlob`  
 [v] Velikost v bajtech `pvSigBlob`.  
  
 `pmb`  
 [out] Ukazatel na odpovídající MethodDef token.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte metodu pomocí jeho nadřazených třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`). Může být několik metod se stejným názvem do třídy nebo rozhraní. V takovém případě předejte signatury metody se najít shodu jedinečný.  
  
 Podpis předaný `FindMethod` musí být vygenerováno v aktuálním oboru, protože podpis je vázána na konkrétní rozsah. Podpis můžete vložit token, který identifikuje nadřazeného typu třídy nebo hodnota. Token je index do místní definice typu tabulky. Nelze vytvořit podpis běhu mimo kontext aktuálního oboru a používání tohoto podpisu jako vstup pro vstup na `FindMethod`.  
  
 `FindMethod` Vyhledá pouze metod, které byly definovány přímo v třídy nebo rozhraní; zděděné metody nenajde.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.MethodInfo>  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
