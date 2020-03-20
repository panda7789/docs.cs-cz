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
ms.openlocfilehash: e855868d18fc6cffdd5d92cfa401606caf45b76c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177563"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout – metoda
Dokončí rozložení polí pro třídu, která byla definována předchozím voláním [metody DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
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
 [v] Token, `mdTypeDef` který určuje třídu, která má být rozložena.  
  
 `dwPackSize`  
 [v] Velikost balení: 1, 2, 4, 8 nebo 16 bajtů. Velikost balení je počet bajtů mezi sousedními poli.  
  
 `rFieldOffsets`  
 [v] Pole [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktur, z nichž každá určuje pole třídy a posun pole v rámci třídy. Ukončete `mdTokenNil`pole pomocí .  
  
 `ulClassSize`  
 [v] Velikost třídy v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Třída je zpočátku definována voláním metody [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) a určením jednoho ze tří rozložení pro pole třídy: automatické, sekvenční nebo explicitní. Za normálních okolností byste použili automatické rozložení a nechali za běhu zvolit nejlepší způsob rozložení polí.  
  
 Můžete však chtít pole rozložena podle uspořádání, které používá nespravovaný kód. V takovém případě zvolte sekvenční nebo explicitní rozložení a volání `SetClassLayout` k dokončení rozložení polí:  
  
- Sekvenční rozložení: Zadejte velikost balení. Pole je zarovnáno podle jeho přirozené velikosti nebo velikosti balení, podle toho, která hodnota má menší posun pole. `rFieldOffsets` Nastaveno `ulClassSize` na nulu.  
  
- Explicitní rozložení: Buď určete posun každého pole, nebo určete velikost třídy a velikost balení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
