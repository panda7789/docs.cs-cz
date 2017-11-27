---
title: "IMetaDataAssemblyImport::FindManifestResourceByName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindManifestResourceByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 492f8a50c421df56d1b2f79d15d86ef3251b401e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a>IMetaDataAssemblyImport::FindManifestResourceByName – metoda
Získá ukazatel na prostředku manifestu se zadaným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [v] Název prostředku.  
  
 `ptkManifestResource`  
 [out] Pole používá k ukládání `mdManifestResource` tokenů metadat, z nichž každý představuje prostředku manifestu.  
  
## <a name="remarks"></a>Poznámky  
 `FindManifestResourceByName` Metoda používá standardní pravidla zaměstnaní modul common language runtime pro řešení odkazů.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
