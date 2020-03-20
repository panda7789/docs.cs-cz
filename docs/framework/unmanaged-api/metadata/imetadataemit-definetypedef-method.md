---
title: IMetaDataEmit::DefineTypeDef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175756"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef – metoda
Vytvoří definici typu pro typ modulu runtime společného jazyka a získá token metadat pro tuto definici typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szTypeDef`  
 [v] Název typu v Unicode.  
  
 `dwTypeDefFlags`  
 [v] `TypeDef` atributy. Toto je bitová maska `CoreTypeAttr` hodnot.  
  
 `tkExtends`  
 [v] Token základní třídy. Musí být buď `mdTypeDef` token `mdTypeRef` nebo token.  
  
 `rtkImplements`  
 [v] Pole tokenů určující rozhraní, které implementuje tato třída nebo rozhraní.  
  
 `ptd`  
 [out] Přiřazen `mdTypeDef` token.  
  
## <a name="remarks"></a>Poznámky  
 Příznak v `dwTypeDefFlags` aplikaci určuje, zda je vytvářený typ běžným typem systému (třída nebo rozhraní) nebo běžným typem systémové hodnoty.  
  
 V závislosti na zadaných parametrech může tato metoda jako `mdInterfaceImpl` vedlejší účinek také vytvořit záznam pro každé rozhraní, které je zděděno nebo implementováno tímto typem. Tato metoda však nevrátí žádný `mdInterfaceImpl` z těchto tokenů. Pokud klient chce později přidat `mdInterfaceImpl` nebo upravit token, musí použít `IMetaDataImport` rozhraní k jejich výčetu. Pokud chcete použít sémantiku `[default]` com rozhraní, měli byste zadat výchozí `rtkImplements`rozhraní jako první prvek v ; vlastní atribut nastavený na třídě bude znamenat, že třída má výchozí `mdInterfaceImpl` rozhraní (což je vždy považováno za první token deklarovaný pro třídu).  
  
 Každý prvek `rtkImplements` pole obsahuje `mdTypeDef` `mdTypeRef` nebo token. Poslední prvek v poli `mdTokenNil`musí být .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
