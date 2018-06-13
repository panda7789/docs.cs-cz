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
ms.openlocfilehash: 48d688b64bbe9330a176ef073e96865b719ff2c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446678"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource – metoda
Vytvoří `ManifestResource` struktury obsahující metadata pro zadanou prostředku manifestu a vrátí token přidružených metadat.  
  
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
 [v] Název prostředku.  
  
 `tkImplementation`  
 [v] Token metadata typu `mdtFile` nebo `mdtAssemblyRef` která se mapuje na zprostředkovateli prostředků. Hodnota NULL označuje, že je soubor, ve kterém se vloží metadata poskytovatele prostředků.  
  
 `dwOffset`  
 [v] Posun na začátek prostředků v rámci tohoto souboru. Pro prostředky v samostatné soubory bude vždy nula. Pokud prostředek je vložen soubor PE (přenosné spustitelný soubor), je to posun objektů BLOB, který se spustí v umístění zadaném v záhlaví souboru cor.h prostředku.  
  
 `dwResourceFlags`  
 [v] Bitová kombinace hodnot příznaku, které určují nastavení vlastností pro definici prostředků.  
  
 `pmdmr`  
 [out] Ukazatel na token vrácený metadat.  
  
## <a name="remarks"></a>Poznámky  
 Jeden `ManifestResource` pro každý prostředek, který je implementována ve všech souborů sestavení musí být definován strukturu metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
