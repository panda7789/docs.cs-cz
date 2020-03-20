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
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175847"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent – metoda
Vytvoří definici události se zadaným podpisem metadat a získá token pro tuto definici události.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `td`  
 [v] Token pro cílovou třídu nebo rozhraní. Toto je `mdTypeDef` `mdTypeDefNil` buď nebo token.  
  
 `szEvent`  
 [v] Název události.  
  
 `dwEventFlags`  
 [v] Příznaky události.  
  
 `tkEventType`  
 [v] Token pro třídu události. Toto `mdTypeDef`je `mdTypeRef`, a `mdTokenNil` nebo token.  
  
 `mdAddOn`  
 [v] Metoda použitá k přihlášení k odběru události nebo null.  
  
 `mdRemoveOn`  
 [v] Metoda použitá k odhlášení z odběru události nebo null.  
  
 `mdFire`  
 [v] Metoda použitá (odvozenou třídou) k navojení události.  
  
 `rmdOtherMethods[]`  
 [v] Pole tokenů pro jiné metody přidružené k události. Pole je ukončeno `mdMethodDefNil` tokenem.  
  
 `pmdEvent`  
 [out] Token metadat přiřazený k události.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
