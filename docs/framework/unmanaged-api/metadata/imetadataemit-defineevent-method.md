---
title: "IMetaDataEmit::DefineEvent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f27c0a01dd795cfcc5399c4115cd6d905629fd7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent – metoda
Vytvoří definici pro události s podpisem Zadaná metadata a získá token tuto definici událostí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [v] Token pro danou cílovou třídu nebo rozhraní. To znamená buď `mdTypeDef` nebo `mdTypeDefNil` tokenu.  
  
 `szEvent`  
 [v] Název události.  
  
 `dwEventFlags`  
 [v] Příznaky událostí.  
  
 `tkEventType`  
 [v] Token pro třídy události. Toto je `mdTypeDef`, `mdTypeRef`, nebo `mdTokenNil` tokenu.  
  
 `mdAddOn`  
 [v] Metoda použitá k odběru události, nebo hodnotu null.  
  
 `mdRemoveOn`  
 [v] Metoda použitá k odhlášení odběru událostí, nebo hodnotu null.  
  
 `mdFire`  
 [v] Metoda použitá k vyvolání události (podle odvozené třídy).  
  
 `rmdOtherMethods[]`  
 [v] Pole tokeny pro jiné metody přidružený k události. Toto pole je byla ukončena s `mdMethodDefNil` tokenu.  
  
 `pmdEvent`  
 [out] Metadata token přiřazené k události.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
