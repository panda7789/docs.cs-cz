---
title: "IMetaDataEmit::SetEventProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8e2089c3f4b4e7677c2ddb9eabc8ee08cfd3695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps – metoda
Nastaví nebo aktualizuje určenou funkci události definované předchozí volání [imetadataemit::defineevent –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `ev`  
 [v] Token událostí.  
  
 `dwEventFlags`  
 [v] Příznaky událostí. Toto je bitová maska s `CorEventAttr` hodnoty.  
  
 `tkEventType`  
 [v] Token pro třídy události. To znamená buď `mdTypeDef` nebo `mdTypeRef` tokenu.  
  
 `mdAddOn`  
 [v] Metoda použitá k odběru události, nebo hodnotu null.  
  
 `mdRemoveOn`  
 [v] Metoda použitá k odhlášení odběru událostí, nebo hodnotu null.  
  
 `mdFire`  
 [v] Metoda použitá k vyvolání události (podle odvozené třídy).  
  
 `rmdOtherMethods[]`  
 [v] Pole tokeny pro jiné metody přidružený k události. Musí být posledním prvkem pole `mdMethodDefNil`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
