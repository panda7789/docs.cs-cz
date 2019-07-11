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
ms.openlocfilehash: c455b5196ceafef924de59e9134b89ed62455520
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737223"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout – metoda
Dokončení rozložení polí pro třídu, která je definována v předchozím volání [definetypedef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [in] `mdTypeDef` Token, který určuje třídy, která se vytvoří rozložení.  
  
 `dwPackSize`  
 [in] Velikost komprimace: 1, 2, 4, 8 nebo 16 bajtů. Počet bajtů mezi sousedící pole je velikost komprimace.  
  
 `rFieldOffsets`  
 [in] Pole [cor_field_offset –](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z nichž každý určuje pole třídy a posun v rámci třídy. Ukončit pole s `mdTokenNil`.  
  
 `ulClassSize`  
 [in] Velikost v bajtech třídy.  
  
## <a name="remarks"></a>Poznámky  
 Zpočátku je třída definovaná pomocí volání [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) metoda a zadáním jednoho z tři rozložení pro pole třídy: automaticky, sekvenční nebo explicitní. Za normálních okolností byste pomocí automatického rozložení a umožní modulu runtime, zvolte nejlepší způsob, jak rozložení polí.  
  
 Však můžete chtít pole neuplatní uspořádání nespravovaný kód používá. V tomto případě zvolte sekvenční nebo explicitní rozložení a volání `SetClassLayout` dokončete rozložení polí:  
  
- Sekvenční rozložení: Zadejte velikost komprimace. Pole je zarovnán podle jeho fyzické velikosti nebo velikosti komprimace, podle toho, která má za následek menší posun pole. Nastavte `rFieldOffsets` a `ulClassSize` na nulu.  
  
- Explicitní rozložení: Zadejte posun každé pole nebo určit třídu velikost a velikost komprimace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
