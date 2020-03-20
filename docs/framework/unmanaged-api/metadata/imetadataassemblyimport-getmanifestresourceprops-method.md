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
ms.openlocfilehash: d87d0d46ede65cf44c84edba92fe246174088a4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177658"
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
 [v] Token, `mdManifestResource` který představuje prostředek, pro který chcete získat vlastnosti.  
  
 `szName`  
 [out] Název prostředku.  
  
 `cchName`  
 [v] Velikost , v širokých `szName`znaků, .  
  
 `pchName`  
 [out] Ukazatel na počet širokých znaků skutečně `szName`vrácených v .  
  
 `ptkImplementation`  
 [out] Ukazatel na `mdFile` token nebo `mdAssemblyRef` token, který představuje soubor nebo sestavení, respektive, který obsahuje prostředek.  
  
 `pdwOffset`  
 [out] Ukazatel na hodnotu, která určuje posun od začátku prostředku v souboru.  
  
 `pdwResourceFlags`  
 [out] Ukazatel na příznaky, které popisují metadata použitá pro prostředek. Hodnota příznaky je kombinací jedné nebo více hodnot [CorManifestResourceFlags.](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
