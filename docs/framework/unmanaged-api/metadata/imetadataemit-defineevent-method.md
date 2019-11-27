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
ms.openlocfilehash: 6966d0ad2fefd8401b19d8e8dcf7776799a066b2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432562"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent – metoda
Vytvoří definici události se zadaným podpisem metadat a získá token této definice události.  
  
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
 pro Token pro cílovou třídu nebo rozhraní. Jedná se o token `mdTypeDef` nebo `mdTypeDefNil`.  
  
 `szEvent`  
 pro Název události.  
  
 `dwEventFlags`  
 pro Příznaky události.  
  
 `tkEventType`  
 pro Token pro třídu Event Toto je `mdTypeDef`, `mdTypeRef`nebo token `mdTokenNil`.  
  
 `mdAddOn`  
 pro Metoda použitá k přihlášení k odběru události nebo hodnota null.  
  
 `mdRemoveOn`  
 pro Metoda použitá k odhlášení odběru události nebo hodnota null.  
  
 `mdFire`  
 pro Použitá metoda (odvozenou třídou) k vyvolání události.  
  
 `rmdOtherMethods[]`  
 pro Pole tokenů pro jiné metody přidružené k události. Pole je ukončeno pomocí `mdMethodDefNil`ho tokenu.  
  
 `pmdEvent`  
 mimo Token metadat přiřazený k události  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
