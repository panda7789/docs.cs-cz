---
title: IMetaDataEmit::SetEventProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: 506e13ad956a01b16e36d8c71737fe0efce4c01b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450318"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps – metoda
Nastaví nebo aktualizuje zadanou funkci události definované předchozím voláním metody [IMetaDataEmit::D efineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ev`  
 pro Token události  
  
 `dwEventFlags`  
 pro Příznaky události. Toto je Bitová maska `CorEventAttr` hodnot.  
  
 `tkEventType`  
 pro Token pro třídu Event Toto je buď `mdTypeDef`, nebo token `mdTypeRef`.  
  
 `mdAddOn`  
 pro Metoda použitá k přihlášení k odběru události nebo hodnota null.  
  
 `mdRemoveOn`  
 pro Metoda použitá k odhlášení odběru události nebo hodnota null.  
  
 `mdFire`  
 pro Použitá metoda (odvozenou třídou) k vyvolání události.  
  
 `rmdOtherMethods[]`  
 pro Pole tokenů pro jiné metody přidružené k události. Poslední prvek pole musí být `mdMethodDefNil`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
