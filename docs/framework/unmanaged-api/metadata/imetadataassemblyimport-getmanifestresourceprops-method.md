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
ms.openlocfilehash: c1792ed0f15f8cfb62567593c9694453650f0bb9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436314"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps – metoda
Získá sadu vlastností prostředku manifestu se zadaným podpisem metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Token `mdManifestResource`, který představuje prostředek, pro který chcete získat vlastnosti.  
  
 `szName`  
 mimo Název prostředku.  
  
 `cchName`  
 pro Velikost v rámci velkých znaků `szName`.  
  
 `pchName`  
 mimo Ukazatel na počet velkých znaků, který je ve skutečnosti vrácen v `szName`.  
  
 `ptkImplementation`  
 mimo Ukazatel na token `mdFile` nebo token `mdAssemblyRef`, který představuje soubor nebo sestavení, v uvedeném pořadí, které obsahuje prostředek.  
  
 `pdwOffset`  
 mimo Ukazatel na hodnotu, která určuje posun na začátek prostředku v rámci souboru.  
  
 `pdwResourceFlags`  
 mimo Ukazatel na příznaky, které popisují metadata použitá u prostředku. Hodnota příznaků je kombinací jedné nebo více hodnot [CorManifestResourceFlags –](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
