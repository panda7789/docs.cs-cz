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
ms.openlocfilehash: 031996813718a074eebab62ff54a2de52b898c22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450211"
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
 [in] `TypeDef` atributy. Toto je Bitová maska `CoreTypeAttr` hodnot.  
  
 `tkExtends`  
 pro Token základní třídy. Musí to být buď `mdTypeDef`, nebo token `mdTypeRef`.  
  
 `rtkImplements`  
 pro Pole tokenů určující rozhraní, které tato třída nebo rozhraní implementuje.  
  
 `ptd`  
 mimo Byl přiřazen token `mdTypeDef`.  
  
## <a name="remarks"></a>Poznámky  
 Příznak v `dwTypeDefFlags` určuje, zda typ, který je vytvářen, je typ odkazu na běžný typ systému (třída nebo rozhraní) nebo běžný typ hodnoty systému.  
  
 V závislosti na zadaných parametrech může tato metoda jako vedlejší efekt vytvořit také záznam `mdInterfaceImpl` pro každé rozhraní, které je zděděno nebo implementováno tímto typem. Tato metoda však nevrací žádné z těchto tokenů `mdInterfaceImpl`. Pokud chce klient později přidat nebo změnit `mdInterfaceImpl` tokenu, musí k zobrazení výčtu použít rozhraní `IMetaDataImport`. Pokud chcete použít sémantiku COM `[default]` rozhraní, měli byste zadat výchozí rozhraní jako první prvek v `rtkImplements`; vlastní atribut nastavený u třídy bude označovat, že třída má výchozí rozhraní (což se vždy předpokládá, že se jedná o první `mdInterfaceImpl` token deklarovaný pro třídu).  
  
 Každý prvek `rtkImplements` pole obsahuje token `mdTypeDef` nebo `mdTypeRef`. Poslední prvek v poli musí být `mdTokenNil`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
