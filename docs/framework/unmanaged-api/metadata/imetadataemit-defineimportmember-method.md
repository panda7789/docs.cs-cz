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
ms.openlocfilehash: 2facc63023a20dd6aaac64d7d036324c31658bc8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501310"
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
 pro Rozhraní [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) , které představuje sestavení, ze kterého je importován cílový člen.  
  
 `pbHashValue`  
 pro Pole, které obsahuje hodnotu hash pro sestavení určené parametrem `pAssemImport` .  
  
 `cbHashValue`  
 pro Počet bajtů v `pbHashValue` poli.  
  
 `pImport`  
 pro Rozhraní [IMetaDataImport](imetadataimport-interface.md) , které představuje obor metadat, ze kterého je importován cílový člen.  
  
 `mbMember`  
 pro Token metadat, který určuje cílového člena. Token může být `mdMethodDef` (pro metodu člena), `mdProperty` (pro vlastnost člena) nebo `mdFieldDef` (pro pole člena).  
  
 `pAssemEmit`  
 pro Rozhraní [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) , které představuje sestavení, do kterého je importován cílový člen.  
  
 `tkParent`  
 pro `mdTypeRef`Token nebo `mdModuleRef` pro typ nebo modul, v uvedeném pořadí, který vlastní cílového člena.  
  
 `pmr`  
 mimo `mdMemberRef`Token, který je definován v aktuálním oboru pro odkaz na člena.  
  
## <a name="remarks"></a>Poznámky  
 `DefineImportMember`Metoda vyhledá člena, určeného parametrem `mbMember` , který je definován v jiném oboru, určeného parametrem `pImport` a načte jeho vlastnosti. Tato informace používá k volání metody [IMetaDataEmit::D efinememberref](imetadataemit-definememberref-method.md) v aktuálním oboru pro vytvoření odkazu na člena.  
  
 Obecně platí, že před použitím `DefineImportMember` metody musíte vytvořit v aktuálním oboru odkaz na typ nebo odkaz na modul pro nadřazenou třídu cílového člena, rozhraní nebo modul. Token metadat pro tento odkaz je pak předán v `tkParent` argumentu. Není nutné vytvářet odkaz na nadřazený člen cílového člena, pokud bude vyřešen později kompilátorem nebo linkerem. Shrnutí:  
  
- Pokud je cílový člen pole nebo metoda, použijte buď metodu [IMetaDataEmit::D efinetyperefbyname](imetadataemit-definetyperefbyname-method.md) , nebo [IMetaDataEmit::D efineimporttype](imetadataemit-defineimporttype-method.md) pro vytvoření odkazu na typ v aktuálním oboru pro nadřazenou třídu člena nebo nadřazené rozhraní.  
  
- Pokud je cílový člen globální proměnnou nebo globální funkcí (tj. není členem třídy nebo rozhraní), použijte metodu [IMetaDataEmit::D efinemoduleref](imetadataemit-definemoduleref-method.md) pro vytvoření odkazu na modul v aktuálním oboru pro nadřazený modul člena.  
  
- Pokud cíl cílového člena bude vyřešen později kompilátorem nebo linkerem, pak předejte `mdTokenNil` `tkParent` . Jediným scénářem, ve kterém se to týká, je, že globální funkce nebo globální proměnná se importují ze souboru. obj, který bude nakonec propojený s aktuálním modulem a Sloučená metadata.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
