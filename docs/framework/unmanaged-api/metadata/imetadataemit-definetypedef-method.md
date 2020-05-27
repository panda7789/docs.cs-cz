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
ms.openlocfilehash: dc064b00e32bb6b1d8c2d0c20f571b35919eae23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009337"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef – metoda
Vytvoří definici typu pro typ modulu CLR (Common Language Runtime) a získá token metadat pro danou definici typu.  
  
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
 pro Název typu v kódování Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atribut. Toto je Bitová maska `CoreTypeAttr` hodnot.  
  
 `tkExtends`  
 pro Token základní třídy. Musí to být buď `mdTypeDef` token, nebo `mdTypeRef` .  
  
 `rtkImplements`  
 pro Pole tokenů určující rozhraní, které tato třída nebo rozhraní implementuje.  
  
 `ptd`  
 mimo `mdTypeDef`Přiřazený token.  
  
## <a name="remarks"></a>Poznámky  
 Příznak v `dwTypeDefFlags` Určuje, zda typ, který je vytvářen, je typ odkazu na běžný typ systému (třída nebo rozhraní) nebo běžný typ hodnoty systému.  
  
 V závislosti na zadaných parametrech může tato metoda jako vedlejší efekt vytvořit také `mdInterfaceImpl` záznam pro každé rozhraní, které je zděděno nebo implementováno tímto typem. Tato metoda však nevrátí žádnou z těchto `mdInterfaceImpl` tokenů. Pokud chce klient později přidat nebo změnit `mdInterfaceImpl` token, musí `IMetaDataImport` k zobrazení výčtu použít rozhraní. Pokud chcete použít sémantiku modelu COM `[default]` rozhraní, měli byste zadat výchozí rozhraní jako první prvek v `rtkImplements` ; vlastní atribut nastavený ve třídě bude označovat, že třída má výchozí rozhraní (což je vždy považováno za první `mdInterfaceImpl` token deklarovaný pro třídu).  
  
 Každý prvek `rtkImplements` pole obsahuje `mdTypeDef` `mdTypeRef` token nebo. Poslední prvek v poli musí být `mdTokenNil` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
