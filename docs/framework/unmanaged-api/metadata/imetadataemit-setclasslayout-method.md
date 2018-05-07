---
title: IMetaDataEmit::SetClassLayout – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e22cf8e540bfdb53ad243640dac110b5750e53e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout – metoda
Dokončení rozložení polí pro třídu, která byla definována voláním předchozí [definetypedef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [v] `mdTypeDef` Token, který určuje třídy pro rozloženy.  
  
 `dwPackSize`  
 [v] Velikost okolních: 1, 2, 4, 8 nebo 16 bajtů. Velikost okolních je počet bajtů mezi sousedící pole.  
  
 `rFieldOffsets`  
 [v] Pole [cor_field_offset –](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z nichž každý určuje pole třídy a pole Posun v rámci třídy. Ukončit pole s `mdTokenNil`.  
  
 `ulClassSize`  
 [v] Velikost v bajtech, třídy.  
  
## <a name="remarks"></a>Poznámky  
 Je třída definovaná původně voláním [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) metoda a zadáním jednoho z tři rozložení pro pole třídy: automaticky, sekvenční nebo explicitní. Za normálních okolností byste pomocí automatického rozložení a dát modulu runtime, zvolte nejlepší způsob, jak rozložení polí.  
  
 Ale můžete chtít pole nastíněny podle uspořádání, který nespravovaného kódu používá. V takovém případě zvolte sekvenční nebo explicitní rozložení a volání `SetClassLayout` k dokončení rozložení polí:  
  
-   Sekvenční rozložení: Zadejte velikost okolních. Pole je zarovnán podle jeho přirozené velikost nebo okolních velikostí, podle toho, která má za následek menší posun pole. Nastavit `rFieldOffsets` a `ulClassSize` na hodnotu nula.  
  
-   Explicitní rozložení: posun každého pole nebo zadejte velikost třídy a okolních velikost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
