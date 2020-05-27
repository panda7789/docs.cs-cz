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
ms.openlocfilehash: 026f5efe195cdb34999b65c5f47de6f68d30e11a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008128"
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
 pro Název prostředku.  
  
 `tkImplementation`  
 pro Token metadat typu `mdtFile` nebo `mdtAssemblyRef` , který se mapuje na poskytovatele prostředků. Hodnota NULL znamená, že soubor, ve kterém jsou vložená metadata, je poskytovatel prostředků.  
  
 `dwOffset`  
 pro Posun na začátek prostředku v rámci souboru. U prostředků v samostatných souborech bude tato hodnota vždy nulová. Pokud je prostředek vložen do přenositelného spustitelného souboru (PE), jedná se o posun objektu BLOB prostředku, který začíná v umístění zadaném v souboru hlaviček cor. h.  
  
 `dwResourceFlags`  
 pro Bitová kombinace hodnot příznaků, které určují nastavení vlastností pro definici prostředků.  
  
 `pmdmr`  
 mimo Ukazatel na vrácený token metadat.  
  
## <a name="remarks"></a>Poznámky  
 `ManifestResource`Pro každý prostředek, který je implementován v každém ze souborů sestavení, musí být definována jedna struktura metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
