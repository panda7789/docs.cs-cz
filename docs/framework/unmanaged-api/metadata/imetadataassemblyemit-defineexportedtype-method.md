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
ms.openlocfilehash: a2eb894a8bac702c30826d1e965c91cae9b259ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType – metoda
Vytvoří `ExportedType` struktura obsahující metadata pro zadaný typ exportovat a vrátí token přidružených metadat.  
  
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
 [v] Název typu export. Pro verze 1.1 modul common language runtime, název typu exportovaný musí přesně shodovat s názvem uvedenému v `TypeDef` typu.  
  
 `tkImplementation`  
 [v] Token určující, kde je implementováno exportovaný typu. Platné hodnoty a jejich přidružené význam jsou:  
  
-   `mdFile` Typ je implementována v jiném souboru v rámci této položky assembly.  
  
-   `mdAssemblyRef` Typ je implementovaná v jiném sestavení.  
  
-   `mdExportedTYpe` Typ vnořen v rámci některého jiného typu.  
  
-   `mdFileNil` Typ je ve stejném souboru jako manifest a není typu vnořené.  
  
 `tkTypeDef`  
 [v] Token pro metadata, která určuje typ export. Tato hodnota je zadána v `TypeDef` tabulky v souboru, který implementuje typu a se týkají jenom v případě, že soubor je v tomto sestavení.  
  
 `dwExportedTypeFlags`  
 [v] Bitovou kombinaci [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) hodnot výčtu, které definují nastavení vlastností pro exportovaný typu.  
  
 `pmdct`  
 [out] Ukazatel na token vrácený metadata, který určuje typ exportovaný.  
  
## <a name="remarks"></a>Poznámky  
 `ExportedType` Pro každý typ, který je zveřejněný prostřednictvím toto sestavení a která je implementovaná v modulu než obsahující manifest musí být definován strukturu metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
