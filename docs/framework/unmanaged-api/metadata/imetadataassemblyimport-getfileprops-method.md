---
title: IMetaDataAssemblyImport::GetFileProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: 78c192f10f629a0c1316ae7af7fc774819f4de8f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007478"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps – metoda
Získá vlastnosti souboru se zadaným podpisem metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mdf`  
 pro `mdFile`Token metadat, který představuje soubor, pro který se mají získat vlastnosti.  
  
 `szName`  
 mimo Jednoduchý název souboru.  
  
 `cchName`  
 pro Velikost ve velkých znakech `szName` .  
  
 `pchName`  
 mimo Počet skutečně vrácených znaků `szName` .  
  
 `ppbHashValue`  
 mimo Ukazatel na hodnotu hash. Toto je hodnota hash pomocí algoritmu SHA-1 souboru.  
  
 `pcbHashValue`  
 mimo Počet velkých znaků v vrácené hodnotě hash.  
  
 `pdwFileFlags`  
 mimo Ukazatel na příznaky, které popisují metadata použitá pro soubor. Hodnota příznaků je kombinací jedné nebo více hodnot [CorFileFlags –](corfileflags-enumeration.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyImport – rozhraní](imetadataassemblyimport-interface.md)
