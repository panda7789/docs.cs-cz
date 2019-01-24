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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 145659e8761b8c7804faf25e47a280a9d4f874b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679029"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource – metoda
Vytvoří `ManifestResource` struktury obsahující metadata pro zadaný prostředek manifestu a vrátí token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [in] Název prostředku.  
  
 `tkImplementation`  
 [in] Token metadat typu `mdtFile` nebo `mdtAssemblyRef` , který se mapuje na poskytovateli prostředků. Hodnota NULL označuje, že je soubor, ve kterém se vloží metadata poskytovatele prostředků.  
  
 `dwOffset`  
 [in] Posun k začátku prostředků v rámci souboru. Pro prostředky v samostatné soubory bude vždy nula. Pokud je prostředek vložený v souboru PE (portable executable), je to posun objektu BLOB, který spouští v umístění zadaném v souboru hlaviček cor.h prostředku.  
  
 `dwResourceFlags`  
 [in] Bitová kombinace hodnot příznaků, které určují nastavení vlastností pro definici prostředků.  
  
 `pmdmr`  
 [out] Ukazatel na token vrácený metadat.  
  
## <a name="remarks"></a>Poznámky  
 Jeden `ManifestResource` struktury metadat musí být definované pro každý prostředek, který je implementován v každém ze souborů sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
