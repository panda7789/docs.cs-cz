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
ms.openlocfilehash: 341972629e18213536919fe53bfae94613b4d6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777644"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember – metoda
Vytvoří odkaz na zadaný člen typ nebo modul je definované mimo aktuální obor, který definuje token pro tento odkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `pAssemImport`  
 [in] [Imetadataassemblyimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní, které představuje sestavení, ze kterého cílový člen importovány.  
  
 `pbHashValue`  
 [in] Pole, která obsahuje hodnotu hash pro sestavení určené parametrem `pAssemImport`.  
  
 `cbHashValue`  
 [in] Počet bajtů `pbHashValue` pole.  
  
 `pImport`  
 [in] [Imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní, které představuje obor metadat, ze kterého cílový člen importovány.  
  
 `mbMember`  
 [in] Token metadat, která určuje, že cílový člen. Token, který může být `mdMethodDef` (pro metodu member), `mdProperty` (pro vlastnost člena), nebo `mdFieldDef` (pro člena pole) token.  
  
 `pAssemEmit`  
 [in] [Imetadataassemblyemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) rozhraní, které představuje sestavení, do kterého se importují cílový člen.  
  
 `tkParent`  
 [in] `mdTypeRef` Nebo `mdModuleRef` token pro tento typ nebo modul, v uvedeném pořadí, které vlastní cílový člen.  
  
 `pmr`  
 [out] `mdMemberRef` Token, který je definován v oboru pro odkaz na člena.  
  
## <a name="remarks"></a>Poznámky  
 `DefineImportMember` Metoda vyhledá člen určené `mbMember`, která je definována v jiném rozsahu určeném `pImport`a načte její vlastnosti. Použije tyto informace k volání [imetadataemit::definememberref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metoda v aktuálním rozsahu. Chcete-li vytvořit odkaz na člena.  
  
 Obecně platí, před použitím `DefineImportMember` metoda, je nutné vytvořit, v aktuálním oboru, odkaz na typ nebo odkaz na modul pro cílový člen nadřazené třídy, rozhraní nebo modulu. Token metadat pro tento odkaz je pak předán `tkParent` argument. Není nutné vytvořit odkaz na nadřazený cílový člen, pokud se dá vyřešit později kompilátoru nebo linkeru. Shrnutí:  
  
- Pokud cílový člen je pole nebo metoda, použijte buď [imetadataemit::definetyperefbyname –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) nebo [imetadataemit::defineimporttype –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) metodu pro vytvoření odkazu typu v aktuálním oboru pro nadřazené třídu nebo rozhraní nadřazeného člena.  
  
- Pokud cílový člen je globální proměnnou nebo globální funkce (to znamená, není členem třídy nebo rozhraní), použijte [imetadataemit::definemoduleref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) metodu pro vytvoření odkazu na modul v aktuálním oboru pro nadřazeného člena modul.  
  
- Pokud cílový člen nadřazené vyřeší později kompilátoru nebo linkeru, pak předejte `mdTokenNil` v `tkParent`. To platí pouze scénář, je při globální funkce nebo globální proměnná je importována ze souboru .obj, který bude nakonec propojené s aktuální modul a sloučí metadata.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
