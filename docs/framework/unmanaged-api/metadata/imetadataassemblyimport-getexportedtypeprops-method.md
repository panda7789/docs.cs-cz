---
title: IMetaDataAssemblyImport::GetExportedTypeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8dd1daf3528bbc642033e254a809c18c3662ff1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779182"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps – metoda
Získá sadu vlastností exportovaný typ s podpisem Zadaná metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mdct`  
 [in] `mdExportedType` Token metadat, který představuje exportovaného typu.  
  
 `szName`  
 [out] Název typu exportované.  
  
 `cchName`  
 [in] Velikost v širokých znaků, z `szName`.  
  
 `pchName`  
 [out] Počet skutečně vrácených v široké znaky `szName`  
  
 `ptkImplementation`  
 [out] `mdFile`, `mdAssemblyRef`, Nebo `mdExportedType` token metadat, který obsahuje nebo povoluje přístup k vlastnosti exportovaného typu.  
  
 `ptkTypeDef`  
 [out] Ukazatel `mdTypeDef` token, který představuje typ v souboru.  
  
 `pdwExportedTypeFlags`  
 [out] Ukazatel na příznaky, které popisují metadata u exportovaného typu. Příznaky hodnota může být jeden nebo více [cortypeattr –](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
