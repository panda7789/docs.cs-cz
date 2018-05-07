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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79c9a54a44ae1751cb8b1b57379ccfd6485f6e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember – metoda
Získá ukazatel na MemberDef token pro pole nebo metoda, která je uzavřena k zadanému <xref:System.Type> a má zadaný název a metadata podpis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [v] Token TypeDef pro třídy nebo rozhraní, která obklopuje člena pro vyhledávání. Pokud je tato hodnota `mdTokenNil`, se provádí vyhledávání pro globální proměnná nebo globální funkce.  
  
 `szName`  
 [v] Název člena pro vyhledávání.  
  
 `pvSigBlob`  
 [v] Ukazatel na podpis binární metadata člena.  
  
 `cbSigBlob`  
 [v] Velikost v bajtech `pvSigBlob`.  
  
 `pmb`  
 [out] Ukazatel na odpovídající MemberDef token.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte člena pomocí jeho nadřazených třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`). Může existovat více členy se stejným názvem do třídy nebo rozhraní. V takovém případě předejte člena podpis se najít shodu jedinečný.  
  
 Podpis předaný `FindMember` musí být vygenerováno v aktuálním oboru, protože podpis je vázána na konkrétní rozsah. Podpis můžete vložit token, který identifikuje nadřazeného typu třídy nebo hodnota. Token je index do místní definice typu tabulky. Nelze vytvořit podpis běhu mimo kontext aktuálního oboru a používání tohoto podpisu jako vstup pro vstup na `FindMember`.  
  
 `FindMember` Vyhledá pouze členové, které byly definovány přímo v třídy nebo rozhraní; zděděné členy nenajde.  
  
> [!NOTE]
>  `FindMember` je metoda helper. Zavolá [imetadataimport::findmethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Pokud toto volání nebyl nalezen odpovídající, `FindMember` pak zavolá [imetadataimport::findfield –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
