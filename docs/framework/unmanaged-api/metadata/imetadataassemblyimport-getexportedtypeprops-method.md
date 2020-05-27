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
ms.openlocfilehash: 944941c2356cae93ecc85f1714b4b29aefcb50ad
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008401"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps – metoda
Získá sadu vlastností exportovaného typu se zadaným podpisem metadat.  
  
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
 pro `mdExportedType`Token metadat, který představuje exportovaný typ.  
  
 `szName`  
 mimo Název exportovaného typu.  
  
 `cchName`  
 pro Velikost (v rámci velkých znaků) `szName` .  
  
 `pchName`  
 mimo Počet skutečně vrácených znaků`szName`  
  
 `ptkImplementation`  
 mimo `mdFile` `mdAssemblyRef` Token metadat, nebo `mdExportedType` , který obsahuje nebo umožňuje přístup k vlastnostem exportovaného typu.  
  
 `ptkTypeDef`  
 mimo Ukazatel na `mdTypeDef` token, který představuje typ v souboru.  
  
 `pdwExportedTypeFlags`  
 mimo Ukazatel na příznaky, které popisují metadata použitá pro exportovaný typ. Hodnota příznaků může být jedna nebo víc hodnot [CorTypeAttr –](cortypeattr-enumeration.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyImport – rozhraní](imetadataassemblyimport-interface.md)
