---
title: "IMetaDataAssemblyEmit::DefineExportedType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59aae188e404ebc717a140fb7918e3fbf69f3f70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
-   `mdFile`Typ je implementována v jiném souboru v rámci této položky assembly.  
  
-   `mdAssemblyRef`Typ je implementovaná v jiném sestavení.  
  
-   `mdExportedTYpe`Typ vnořen v rámci některého jiného typu.  
  
-   `mdFileNil`Typ je ve stejném souboru jako manifest a není typu vnořené.  
  
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
