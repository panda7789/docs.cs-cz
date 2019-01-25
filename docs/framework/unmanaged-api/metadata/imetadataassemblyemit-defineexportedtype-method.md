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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 071466858c79fdb74d9055fed09990cdb02a88b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624340"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType – metoda
Vytvoří `ExportedType` struktura obsahující metadata pro zadanou exportovat typ a vrátí token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [in] Název typu nelze exportovat. Pro verze 1.1 modul common language runtime, název typu exportované musí přesně shodovat s názvem podle `TypeDef` typu.  
  
 `tkImplementation`  
 [in] Token určující, kde se exportovaný typ implementuje. Platné hodnoty a jejich přidružené vysvětlení jsou:  
  
-   `mdFile` Typ je implementována do jiného souboru v rámci tohoto sestavení.  
  
-   `mdAssemblyRef` Typ je implementované v jiném sestavení.  
  
-   `mdExportedTYpe` Typ je vnořená v rámci některého jiného typu.  
  
-   `mdFileNil` Typ je ve stejném souboru jako manifest a není vnořeného typu.  
  
 `tkTypeDef`  
 [in] Token pro metadata, která určuje typ, který chcete exportovat. Tato hodnota se zadá v `TypeDef` tabulky v souboru, který implementuje typ a je relevantní pouze v případě, že tento soubor je v tomto sestavení.  
  
 `dwExportedTypeFlags`  
 [in] Bitová kombinace hodnot [cortypeattr –](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) hodnot výčtu, která definují nastavení vlastností pro exportovaný typ.  
  
 `pmdct`  
 [out] Ukazatel na token vrácených metadat, který určuje exportovaný typ.  
  
## <a name="remarks"></a>Poznámky  
 `ExportedType` Struktury metadat musí být definované pro každý typ, který je zveřejněný prostřednictvím tohoto sestavení a je implementována v modulu než ten, který obsahuje manifest.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
