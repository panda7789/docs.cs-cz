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
ms.openlocfilehash: beb697d80417b937876a0887e4376341185a47d9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447208"
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
 pro Token metadat `mdFile`, který představuje soubor, pro který se mají získat vlastnosti.  
  
 `szName`  
 mimo Jednoduchý název souboru.  
  
 `cchName`  
 pro Velikost v rámci velkých znaků `szName`.  
  
 `pchName`  
 mimo Počet znaků, které jsou ve skutečnosti vraceny `szName`.  
  
 `ppbHashValue`  
 mimo Ukazatel na hodnotu hash. Toto je hodnota hash pomocí algoritmu SHA-1 souboru.  
  
 `pcbHashValue`  
 mimo Počet velkých znaků v vrácené hodnotě hash.  
  
 `pdwFileFlags`  
 mimo Ukazatel na příznaky, které popisují metadata použitá pro soubor. Hodnota příznaků je kombinací jedné nebo více hodnot [CorFileFlags –](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
