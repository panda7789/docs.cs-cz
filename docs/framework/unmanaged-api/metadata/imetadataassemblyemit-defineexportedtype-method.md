---
title: IMetaDataAssemblyEmit::DefineExportedType – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 44f97ef498eb8e64c55fc86b9f290b9e088293f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432065"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType – metoda
Vytvoří strukturu `ExportedType` obsahující metadata pro zadaný exportovaný typ a vrátí přidružený token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 pro Název typu, který má být exportován. Pro verzi 1,1 modulu Common Language Runtime musí název exportovaného typu přesně odpovídat názvu uvedenému v `TypeDef` pro daný typ.  
  
 `tkImplementation`  
 pro Token určující, kde je implementován exportovaný typ. Platné hodnoty a jejich přidružené významy jsou:  
  
- `mdFile` je typ implementován v jiném souboru v rámci tohoto sestavení.  
  
- `mdAssemblyRef` typ je implementován v jiném sestavení.  
  
- `mdExportedTYpe` je typ vnořen v jiném typu.  
  
- `mdFileNil` typ je ve stejném souboru jako manifest a není vnořený typ.  
  
 `tkTypeDef`  
 pro Token metadat, který určuje typ, který má být exportován. Tato hodnota je zadána v tabulce `TypeDef` v souboru, který implementuje typ a je relevantní pouze v případě, že tento soubor je v tomto sestavení.  
  
 `dwExportedTypeFlags`  
 pro Bitová kombinace hodnot výčtu [CorTypeAttr –](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) , která definuje nastavení vlastností pro exportovaný typ.  
  
 `pmdct`  
 mimo Ukazatel na vrácený token metadat, který označuje exportovaný typ.  
  
## <a name="remarks"></a>Poznámky  
 `ExportedType` struktura metadat musí být definována pro každý typ, který je vystaven tímto sestavením a který je implementován v jiném modulu než ten, který obsahuje manifest.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
