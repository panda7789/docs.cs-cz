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
ms.openlocfilehash: c0b6d53ce3be3aed6a577bf6e38a281928499848
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009025"
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
 pro `mdManifestResource`Token, který představuje prostředek, pro který chcete získat vlastnosti.  
  
 `szName`  
 mimo Název prostředku.  
  
 `cchName`  
 pro Velikost ve velkých znakech `szName` .  
  
 `pchName`  
 mimo Ukazatel na počet velkých znaků, které se ve skutečnosti vrátily `szName` .  
  
 `ptkImplementation`  
 mimo Ukazatel na `mdFile` token nebo `mdAssemblyRef` token, který představuje soubor nebo sestavení, v uvedeném pořadí, které obsahuje prostředek.  
  
 `pdwOffset`  
 mimo Ukazatel na hodnotu, která určuje posun na začátek prostředku v rámci souboru.  
  
 `pdwResourceFlags`  
 mimo Ukazatel na příznaky, které popisují metadata použitá u prostředku. Hodnota příznaků je kombinací jedné nebo více hodnot [CorManifestResourceFlags –](cormanifestresourceflags-enumeration.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyImport – rozhraní](imetadataassemblyimport-interface.md)
