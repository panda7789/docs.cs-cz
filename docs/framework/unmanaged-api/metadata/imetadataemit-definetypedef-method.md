---
title: "IMetaDataEmit::DefineTypeDef – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeDef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da8fed37605252139428aa40bb3785c242d95cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef – metoda
Vytvoří definici typu pro běžné typ modulu runtime jazyka a získá metadata token pro tuto definici typu.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `szTypeDef`  
 [v] Název typu ve formátu Unicode.  
  
 `dwTypeDefFlags`  
 [v] `TypeDef` atributy. Toto je bitová maska s `CoreTypeAttr` hodnoty.  
  
 `tkExtends`  
 [v] Token základní třídy. Musí být buď `mdTypeDef` nebo `mdTypeRef` tokenu.  
  
 `rtkImplements`  
 [v] Pole určující rozhraní, která implementuje této třídě nebo rozhraní tokeny.  
  
 `ptd`  
 [out] `mdTypeDef` Token přiřazený.  
  
## <a name="remarks"></a>Poznámky  
 Příznak v `dwTypeDefFlags` Určuje, jestli je typ vytváří běžné typ systému typu odkazu (třídy nebo rozhraní) nebo společné typ hodnoty systému typu.  
  
 V závislosti na parametry zadané, tato metoda jako vedlejším účinkem, může taky vytvořit `mdInterfaceImpl` záznamu pro každý rozhraní, které je zděděná nebo implementované tohoto typu. Však tato metoda nevrátí žádné z těchto `mdInterfaceImpl` tokeny. Pokud klient chce později přidat nebo upravit `mdInterfaceImpl` tokenu, musí používat `IMetaDataImport` rozhraní je výčet. Pokud chcete použít sémantiku COM `[default]` rozhraní, musí zadat výchozí rozhraní jako prvním elementem v `rtkImplements`; vlastních atributů, nastavte u třídy bude znamenat, že třída má výchozí rozhraní (což je vždy předpokládá, že se nejprve `mdInterfaceImpl` token deklarovaný pro třídu).  
  
 Každý element `rtkImplements` pole blokování `mdTypeDef` nebo `mdTypeRef` tokenu. Musí být posledním prvkem v poli `mdTokenNil`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
