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
ms.openlocfilehash: 720133e64c02aa09c9ff7e43a20630b0d55c1acf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008752"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps – metoda
Nastaví nebo aktualizuje zadanou funkci události definované předchozím voláním metody [IMetaDataEmit::D efineevent](imetadataemit-defineevent-method.md).  
  
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
 pro Token pro třídu Event Toto je buď `mdTypeDef` token, nebo `mdTypeRef` .  
  
 `mdAddOn`  
 pro Metoda použitá k přihlášení k odběru události nebo hodnota null.  
  
 `mdRemoveOn`  
 pro Metoda použitá k odhlášení odběru události nebo hodnota null.  
  
 `mdFire`  
 pro Použitá metoda (odvozenou třídou) k vyvolání události.  
  
 `rmdOtherMethods[]`  
 pro Pole tokenů pro jiné metody přidružené k události. Poslední prvek pole musí být `mdMethodDefNil` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
