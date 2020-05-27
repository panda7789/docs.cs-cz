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
ms.openlocfilehash: 81d6c972b53221ee53cbcf31639d65c30858b48b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008154"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType – metoda
Vytvoří `ExportedType` strukturu obsahující metadata pro zadaný exportovaný typ a vrátí přidružený token metadat.  
  
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
 pro Název typu, který má být exportován. Pro verzi 1,1 modulu CLR musí název exportovaného typu přesně odpovídat názvu uvedenému v poli `TypeDef` pro typ.  
  
 `tkImplementation`  
 pro Token určující, kde je implementován exportovaný typ. Platné hodnoty a jejich přidružené významy jsou:  
  
- `mdFile`Typ je implementován v jiném souboru v tomto sestavení.  
  
- `mdAssemblyRef`Typ je implementován v jiném sestavení.  
  
- `mdExportedTYpe`Typ je vnořen v jiném typu.  
  
- `mdFileNil`Typ je ve stejném souboru jako manifest a není vnořený typ.  
  
 `tkTypeDef`  
 pro Token metadat, který určuje typ, který má být exportován. Tato hodnota je zadána v `TypeDef` tabulce v souboru, který implementuje typ a je relevantní pouze v případě, že tento soubor je v tomto sestavení.  
  
 `dwExportedTypeFlags`  
 pro Bitová kombinace hodnot výčtu [CorTypeAttr –](cortypeattr-enumeration.md) , která definuje nastavení vlastností pro exportovaný typ.  
  
 `pmdct`  
 mimo Ukazatel na vrácený token metadat, který označuje exportovaný typ.  
  
## <a name="remarks"></a>Poznámky  
 `ExportedType`Struktura metadat musí být definována pro každý typ, který je vystaven tímto sestavením a který je implementován v jiném modulu než ten, který obsahuje manifest.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
