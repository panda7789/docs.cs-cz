---
title: "IMetaDataAssemblyImport::GetManifestResourceProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetManifestResourceProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ba9af4abca111b94a678c48d236a53dc6313b21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps – metoda
Získá sadu vlastností prostředku manifestu podpisem Zadaná metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mdmr`  
 [v] `mdManifestResource` Token, který představuje prostředků, pro které chcete získat vlastnosti.  
  
 `szName`  
 [out] Název prostředku.  
  
 `cchName`  
 [v] Velikost v široké znaků, z `szName`.  
  
 `pchName`  
 [out] Ukazatel na počet široké znaků ve skutečnosti, vrátí se v `szName`.  
  
 `ptkImplementation`  
 [out] Ukazatel na `mdFile` tokenu nebo `mdAssemblyRef` token, který představuje soubor nebo sestavení, v uvedeném pořadí, který obsahuje prostředek.  
  
 `pdwOffset`  
 [out] Ukazatel na hodnotu, která určuje posun na začátek prostředků v rámci tohoto souboru.  
  
 `pdwResourceFlags`  
 [out] Ukazatel na příznaky, které popisují metadata u prostředku. Hodnota příznaky je kombinací jednoho nebo více [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
