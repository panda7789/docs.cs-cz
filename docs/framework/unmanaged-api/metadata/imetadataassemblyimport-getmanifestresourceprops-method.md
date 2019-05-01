---
title: IMetaDataAssemblyImport::GetManifestResourceProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba99d84686974b425bcdee0bbf4770e4843e1351
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992573"
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
  
## <a name="parameters"></a>Parametry  
 `mdmr`  
 [in] `mdManifestResource` Token, který představuje prostředek, pro které chcete získat vlastnosti.  
  
 `szName`  
 [out] Název prostředku.  
  
 `cchName`  
 [in] Velikost v široké znaky z `szName`.  
  
 `pchName`  
 [out] Ukazatel na počet skutečně vrácených v široké znaky `szName`.  
  
 `ptkImplementation`  
 [out] Ukazatel `mdFile` token nebo `mdAssemblyRef` token představující soubor nebo sestavení, v uvedeném pořadí, který obsahuje prostředek.  
  
 `pdwOffset`  
 [out] Ukazatel na hodnotu, která určuje posun na začátek prostředků v rámci souboru.  
  
 `pdwResourceFlags`  
 [out] Ukazatel na příznaky, které popisují metadata pro prostředek použito. Hodnota příznaků je kombinace jedné nebo více [cormanifestresourceflags –](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
