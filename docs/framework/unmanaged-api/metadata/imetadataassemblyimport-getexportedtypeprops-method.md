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
ms.openlocfilehash: 82302124828a2dab73b445128d7d847e112edd36
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448219"
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
 pro Token metadat `mdExportedType`, který představuje exportovaný typ.  
  
 `szName`  
 mimo Název exportovaného typu.  
  
 `cchName`  
 pro Velikost `szName`v různých znacích.  
  
 `pchName`  
 mimo Počet skutečně vrácených znaků v `szName`  
  
 `ptkImplementation`  
 mimo Token metadat `mdFile`, `mdAssemblyRef`nebo `mdExportedType`, který obsahuje nebo umožňuje přístup k vlastnostem exportovaného typu.  
  
 `ptkTypeDef`  
 mimo Ukazatel na token `mdTypeDef`, který představuje typ v souboru.  
  
 `pdwExportedTypeFlags`  
 mimo Ukazatel na příznaky, které popisují metadata použitá pro exportovaný typ. Hodnota příznaků může být jedna nebo víc hodnot [CorTypeAttr –](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
