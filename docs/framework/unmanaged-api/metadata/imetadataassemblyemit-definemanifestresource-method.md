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
ms.openlocfilehash: 83170815f4aa65988bb6a6394bd466a0ba376ebf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432062"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource – metoda
Vytvoří strukturu `ManifestResource` obsahující metadata pro zadaný prostředek manifestu a vrátí přidružený token metadat.  
  
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
 pro Název prostředku.  
  
 `tkImplementation`  
 pro Token metadat typu `mdtFile` nebo `mdtAssemblyRef`, který se mapuje na poskytovatele prostředků. Hodnota NULL znamená, že soubor, ve kterém jsou vložená metadata, je poskytovatel prostředků.  
  
 `dwOffset`  
 pro Posun na začátek prostředku v rámci souboru. U prostředků v samostatných souborech bude tato hodnota vždy nulová. Pokud je prostředek vložen do přenositelného spustitelného souboru (PE), jedná se o posun objektu BLOB prostředku, který začíná v umístění zadaném v souboru hlaviček cor. h.  
  
 `dwResourceFlags`  
 pro Bitová kombinace hodnot příznaků, které určují nastavení vlastností pro definici prostředků.  
  
 `pmdmr`  
 mimo Ukazatel na vrácený token metadat.  
  
## <a name="remarks"></a>Poznámky  
 Pro každý prostředek, který je implementován v každém souboru sestavení, musí být definována jedna `ManifestResource` struktura metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
