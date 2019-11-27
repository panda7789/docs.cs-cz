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
ms.openlocfilehash: 75711b3d87699ff5db21a04351ff0acaccabb5aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431857"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember – metoda
Vytvoří odkaz na zadaného člena typu nebo modulu, který je definován mimo aktuální obor, a definuje token pro tento odkaz.  
  
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
 pro Rozhraní [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) , které představuje sestavení, ze kterého je importován cílový člen.  
  
 `pbHashValue`  
 pro Pole, které obsahuje hodnotu hash pro sestavení určené parametrem `pAssemImport`.  
  
 `cbHashValue`  
 pro Počet bajtů v poli `pbHashValue`.  
  
 `pImport`  
 pro Rozhraní [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , které představuje obor metadat, ze kterého je importován cílový člen.  
  
 `mbMember`  
 pro Token metadat, který určuje cílového člena. Token může být `mdMethodDef` (pro metodu člena), `mdProperty` (pro vlastnost člena) nebo `mdFieldDef` (pro pole člena).  
  
 `pAssemEmit`  
 pro Rozhraní [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) , které představuje sestavení, do kterého je importován cílový člen.  
  
 `tkParent`  
 pro Token `mdTypeRef` nebo `mdModuleRef` pro typ nebo modul, v uvedeném pořadí, který vlastní cílového člena.  
  
 `pmr`  
 mimo Token `mdMemberRef`, který je definován v aktuálním oboru pro odkaz na člena.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `DefineImportMember` vyhledá člena, určeného parametrem `mbMember`, který je definován v jiném oboru určeném `pImport`a načte jeho vlastnosti. Tato informace používá k volání metody [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) v aktuálním oboru pro vytvoření odkazu na člena.  
  
 Obecně platí, že před použitím metody `DefineImportMember` musíte vytvořit v aktuálním oboru odkaz na typ nebo odkaz na modul pro nadřazenou třídu cílového člena, rozhraní nebo modul. Token metadat pro tento odkaz je pak předán v argumentu `tkParent`. Není nutné vytvářet odkaz na nadřazený člen cílového člena, pokud bude vyřešen později kompilátorem nebo linkerem. Sumarizace:  
  
- Pokud je cílový člen pole nebo metoda, použijte buď metodu [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) , nebo [IMetaDataEmit::D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) pro vytvoření odkazu na typ v aktuálním oboru pro nadřazenou třídu člena nebo nadřazené rozhraní.  
  
- Pokud je cílový člen globální proměnnou nebo globální funkcí (tj. není členem třídy nebo rozhraní), použijte metodu [IMetaDataEmit::D efinemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) pro vytvoření odkazu na modul v aktuálním oboru pro nadřazený modul člena.  
  
- Pokud cíl cílového člena bude vyřešen později kompilátorem nebo linkerem, pak předejte `mdTokenNil` v `tkParent`. Jediným scénářem, ve kterém se to týká, je, že globální funkce nebo globální proměnná se importují ze souboru. obj, který bude nakonec propojený s aktuálním modulem a Sloučená metadata.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
