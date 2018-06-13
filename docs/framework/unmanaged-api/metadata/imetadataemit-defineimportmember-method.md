---
title: IMetaDataEmit::DefineImportMember – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f9995fda70d1d5a3c19c30496de6c32f20015d47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449387"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember – metoda
Vytvoří odkaz na zadaný člen typu nebo modul, který je definován v aktuálním oboru a definuje token pro tento odkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAssemImport`  
 [v] [Imetadataassemblyimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní, které představuje sestavení, ze kterého je naimportované cílového člena.  
  
 `pbHashValue`  
 [v] Pole, které obsahuje hodnotu hash pro sestavení určeného `pAssemImport`.  
  
 `cbHashValue`  
 [v] Počet bajtů `pbHashValue` pole.  
  
 `pImport`  
 [v] [Imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní, které představuje metadata oboru, ze kterého je naimportována cílového člena.  
  
 `mbMember`  
 [v] Metadata token, který určuje cíl člena. Může být token `mdMethodDef` (pro metodu člen), `mdProperty` (pro vlastnost člena), nebo `mdFieldDef` (pro pole člen) tokenu.  
  
 `pAssemEmit`  
 [v] [Imetadataassemblyemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) rozhraní, které představuje sestavení, do kterého je naimportované cílového člena.  
  
 `tkParent`  
 [v] `mdTypeRef` Nebo `mdModuleRef` tokenu pro modul nebo typ, v uvedeném pořadí, který je vlastníkem člen cíl.  
  
 `pmr`  
 [out] `mdMemberRef` Token, který je definován v aktuálním oboru pro odkaz na člena.  
  
## <a name="remarks"></a>Poznámky  
 `DefineImportMember` Metoda vyhledá člena, zadán `mbMember`, která je definována v jiném oboru určeného `pImport`a načte její vlastnosti. Tyto informace se použijí k volání [imetadataemit::definememberref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metoda v aktuálním oboru vytvořit odkaz na člena.  
  
 Obecně platí, před použitím `DefineImportMember` metoda, je nutné vytvořit, v aktuálním oboru, odkaz na typ nebo odkaz na modul pro nadřazené třídy, rozhraní nebo modul člen cíl. Metadata token u tohoto odkazu je pak předaná `tkParent` argument. Není nutné vytvořit odkaz na nadřazený člen cíl, pokud bude vyřešen později kompilátoru nebo linkeru. Shrnutí:  
  
-   Pokud je člen cílového pole nebo metoda, použijte buď [imetadataemit::definetyperefbyname –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) nebo [imetadataemit::defineimporttype –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) metodu pro vytvoření odkaz na typ, v aktuálním oboru pro nadřazené třídy nebo rozhraní nadřazeného člena.  
  
-   Pokud je cílový člen globální proměnné nebo globální funkce (to znamená, nikoli pro člena třídy nebo rozhraní), použijte [imetadataemit::definemoduleref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) metodu pro vytvoření odkazu na modul v aktuálním oboru pro nadřazeného člena modul.  
  
-   Pokud cílový člen nadřazené vyřeší později kompilátoru nebo linkeru, pak předejte `mdTokenNil` v `tkParent`. Jediný scénář, ve kterém platí je při globální funkce nebo – globální proměnná importována ze souboru .obj, který se nakonec propojené do aktuální modul a metadata sloučit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
