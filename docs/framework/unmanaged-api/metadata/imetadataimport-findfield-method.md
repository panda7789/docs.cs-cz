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
ms.openlocfilehash: ac69bab45ccd39b6a055fe4d2f74950ab47da779
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField – metoda
Získá ukazatel na FieldDef token pole, která je uzavřena k zadanému <xref:System.Type> a má zadaný název a metadata podpis.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [v] Token TypeDef pro třídy nebo rozhraní, která obklopuje pole pro vyhledávání. Pokud je tato hodnota `mdTokenNil`, globální proměnné se provádí vyhledávání.  
  
 `szName`  
 [v] Název pole, které chcete vyhledat.  
  
 `pvSigBlob`  
 [v] Ukazatel na binární metadata podpis pole.  
  
 `cbSigBlob`  
 [v] Velikost v bajtech `pvSigBlob`.  
  
 `pmb`  
 [out] Ukazatel na odpovídající FieldDef token.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte pole, které používá jeho nadřazených třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).  
  
 Podpis předaný `FindField` musí být vygenerováno v aktuálním oboru, protože podpis je vázána na konkrétní rozsah. Podpis můžete vložit token, který identifikuje nadřazeného typu třídy nebo hodnota. (Token je index do místní tabulky TypeDef). Nelze vytvořit podpis běhu mimo kontext aktuálního oboru a použít jako vstup pro tento podpis `FindField`.  
  
 `FindField` Vyhledá pouze pole, které byly definovány přímo v třídy nebo rozhraní; zděděné pole nenajde.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
