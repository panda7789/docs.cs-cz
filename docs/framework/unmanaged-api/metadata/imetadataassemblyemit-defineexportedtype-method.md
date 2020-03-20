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
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177882"
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
 [v] Název typu, který má být exportován. Pro verzi 1.1 za běhu společného jazyka musí název exportovaného typu `TypeDef` přesně odpovídat názvu uvedenému v pro typ.  
  
 `tkImplementation`  
 [v] Token určující, kde je implementován exportovaný typ. Platné hodnoty a jejich přidružené významy jsou:  
  
- `mdFile`Typ je implementován v jiném souboru v rámci tohoto sestavení.  
  
- `mdAssemblyRef`Typ je implementován v jiném sestavení.  
  
- `mdExportedTYpe`Typ je vnořen do jiného typu.  
  
- `mdFileNil`Typ je ve stejném souboru jako manifest a není vnořený typ.  
  
 `tkTypeDef`  
 [v] Token metadat, který určuje typ, který má být exportován. Tato hodnota je `TypeDef` zadána v tabulce v souboru, který implementuje typ a je relevantní pouze v případě, že tento soubor je v tomto sestavení.  
  
 `dwExportedTypeFlags`  
 [v] Bitová kombinace hodnot výčtu [CorTypeAttr,](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) které definují nastavení vlastností exportovaného typu.  
  
 `pmdct`  
 [out] Ukazatel na vrácený token metadat, který označuje exportovaný typ.  
  
## <a name="remarks"></a>Poznámky  
 Struktura `ExportedType` metadat musí být definována pro každý typ, který je vystaven tímto sestavením a který je implementován v modulu než ten, který obsahuje manifest.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
