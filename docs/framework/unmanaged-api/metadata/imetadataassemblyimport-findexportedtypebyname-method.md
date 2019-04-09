---
title: IMetaDataAssemblyImport::FindExportedTypeByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32a7b7b498cc4e52b8be3f43ae52293de380d9f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182257"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a>IMetaDataAssemblyImport::FindExportedTypeByName – metoda
Získá ukazatel na exportovaný typ daného názvu a nadřazený typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 [in] Název typu exportované.  
  
 `mdtExportedType`  
 [in] Token metadat pro nadřazené třídu exportovaného typu. Tato hodnota je `mdExportedTypeNil` Pokud požadovaný export typu není vnořeného typu.  
  
 `ptkExportedType`  
 [out] Ukazatel `mdExportedType` token, který představuje exportovaného typu.  
  
## <a name="remarks"></a>Poznámky  
 `FindExportedTypeByName` Metoda používá standardní pravidla náhradník modul common language runtime k vyřešení odkazů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [Jak běhové prostředí vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
