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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b6f5881f289bed258191baf4f43264ea6ba35db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141801"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef – metoda
Vytvoří definici typu pro společný typ modulu runtime jazyka a získá token metadat pro tuto definici typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Název typu v kódování Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atributy. To je bitová maska z `CoreTypeAttr` hodnoty.  
  
 `tkExtends`  
 [in] Token základní třídy. Musí se jednat buď `mdTypeDef` nebo `mdTypeRef` token.  
  
 `rtkImplements`  
 [in] Pole tokeny zadání rozhraní, které implementuje Tato třída nebo rozhraní.  
  
 `ptd`  
 [out] `mdTypeDef` Token přiřazený.  
  
## <a name="remarks"></a>Poznámky  
 Příznak v `dwTypeDefFlags` Určuje, zda je typ vytváří společný typ systému typem odkazu (třídy nebo rozhraní) nebo na společný typ. hodnota typu systému.  
  
 V závislosti na zadaných parametrů této metody jako vedlejší účinek, může také vytvořit `mdInterfaceImpl` záznamů pro každé rozhraní, které je zděděná nebo implementovaný tímto typem. Ale tato metoda nevrátí žádnou z těchto `mdInterfaceImpl` tokeny. Pokud klient požaduje později přidat nebo upravit `mdInterfaceImpl` tokenu, je nutné použít `IMetaDataImport` rozhraní je výčet. Pokud chcete použít sémantika COM `[default]` rozhraní, by mělo nabízet výchozí rozhraní jako první prvek v `rtkImplements`; vlastní atribut nastaven na třídy bude označovat, že třída nemá výchozí rozhraní (což je vždy považován za nejprve `mdInterfaceImpl` token deklarované třídy).  
  
 Každý prvek `rtkImplements` pole obsahuje `mdTypeDef` nebo `mdTypeRef` token. Poslední prvek v poli musí být `mdTokenNil`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
