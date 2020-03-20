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
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175860"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember – metoda
Vytvoří odkaz na zadaný člen typu nebo modulu, který je definován mimo aktuální obor a definuje token pro tento odkaz.  
  
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
 [v] Rozhraní [IMetaDataAssemblyImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) které představuje sestavení, ze kterého je importován cílový člen.  
  
 `pbHashValue`  
 [v] Pole, které obsahuje hash pro `pAssemImport`sestavení určené .  
  
 `cbHashValue`  
 [v] Počet bajtů v `pbHashValue` poli.  
  
 `pImport`  
 [v] Rozhraní [IMetaDataImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) které představuje obor metadat, ze kterého je importován cílový člen.  
  
 `mbMember`  
 [v] Token metadat, který určuje cílový člen. Token může být `mdMethodDef` token (pro `mdProperty` metodu člena), (pro vlastnost člena) nebo `mdFieldDef` (pro členské pole) token.  
  
 `pAssemEmit`  
 [v] Rozhraní [IMetaDataAssemblyEmit,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) které představuje sestavení, do kterého je importován cílový člen.  
  
 `tkParent`  
 [v] `mdModuleRef` Nebo `mdTypeRef` token pro typ nebo modul, respektive, který vlastní cílový člen.  
  
 `pmr`  
 [out] Token, `mdMemberRef` který je definován v aktuálním oboru pro odkaz na člena.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `DefineImportMember` vyhledá člen, určený `mbMember`v , který je definován `pImport`v jiném oboru, určený v . a načte jeho vlastnosti. Tyto informace používá k volání [metody IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) v aktuálním oboru k vytvoření odkazu na člena.  
  
 Obecně platí, že `DefineImportMember` před použitím metody je nutné vytvořit v aktuálním oboru odkaz na typ nebo odkaz na modul pro nadřazenou třídu, rozhraní nebo modul cílového člena. Token metadat pro tento odkaz je `tkParent` pak předán v argumentu. Není nutné vytvořit odkaz na nadřazený cílový člen, pokud bude vyřešen později kompilátorem nebo propojovacím sítí. Shrnutí:  
  
- Pokud je cílovým členem pole nebo metoda, použijte buď [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) nebo [Metodu IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) k vytvoření odkazu na typ v aktuálním oboru pro nadřazenou třídu člena nebo nadřazené rozhraní.  
  
- Pokud cílový člen je globální proměnná nebo globální funkce (to znamená, že není členem třídy nebo rozhraní), použijte [metodu IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) k vytvoření odkazu na modul v aktuálním oboru pro nadřazený modul člena.  
  
- Pokud nadřazený cílový člen bude vyřešen později kompilátorem nebo propojovacím sítí, pak předajte `mdTokenNil` `tkParent`. Jediný scénář, ve kterém to platí je, když globální funkce nebo globální proměnná je importován ze souboru OBJ, který bude nakonec propojeny do aktuálního modulu a metadata sloučena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
