---
title: IMetaDataEmit::DefineEvent – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7d42fe17af5b10d718d0e2b6a7ae33644fa4813
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730292"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent – metoda
Vytvoří definici pro události s podpisem Zadaná metadata a získá token pro tuto definici událostí.  
  
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
 [in] Token pro cílovou třídu nebo rozhraní. Je to `mdTypeDef` nebo `mdTypeDefNil` token.  
  
 `szEvent`  
 [in] Název události.  
  
 `dwEventFlags`  
 [in] Příznaky událostí.  
  
 `tkEventType`  
 [in] Token pro třídy události. Jde `mdTypeDef`, `mdTypeRef`, nebo `mdTokenNil` token.  
  
 `mdAddOn`  
 [in] Metoda použitá k přihlášení k odběru událostí, nebo hodnotu null.  
  
 `mdRemoveOn`  
 [in] Metoda použitá k odhlášení odběru událostí, nebo hodnotu null.  
  
 `mdFire`  
 [in] Metoda použitá pro vyvolání události (prostřednictvím odvozené třídy).  
  
 `rmdOtherMethods[]`  
 [in] Pole tokenů pro jiné metody přidružené k události. Pole je přerušen skrze `mdMethodDefNil` token.  
  
 `pmdEvent`  
 [out] Token metadat přiřazený k této události.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
