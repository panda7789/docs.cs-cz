---
title: IMetaDataAssemblyEmit::DefineManifestResource – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177861"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource – metoda
Vytvoří `ManifestResource` strukturu obsahující metadata pro zadaný prostředek manifestu a vrátí přidružený token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 [v] Název prostředku.  
  
 `tkImplementation`  
 [v] Token metadat typu `mdtFile` nebo `mdtAssemblyRef` který se mapuje na poskytovatele prostředků. Hodnota NULL označuje, že soubor, ve kterém jsou metadata vložena, je poskytovatelem prostředků.  
  
 `dwOffset`  
 [v] Posun na začátek prostředku v souboru. Pro prostředky v samostatných souborech to bude vždy nula. Pokud je prostředek vložen do souboru PE (přenosný spustitelný soubor), jedná se o posun objektu BLOB prostředku, který začíná v umístění určeném v souboru hlavičky cor.h.  
  
 `dwResourceFlags`  
 [v] Bitová kombinace hodnot příznaku, které určují nastavení vlastností pro definici prostředku.  
  
 `pmdmr`  
 [out] Ukazatel na vrácený token metadat.  
  
## <a name="remarks"></a>Poznámky  
 Pro `ManifestResource` každý prostředek, který je implementován v každém souboru sestavení, musí být definována jedna struktura metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
