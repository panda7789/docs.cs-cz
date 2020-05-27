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
ms.openlocfilehash: a18583ce807ffa672811f3a0cd1e744233f6eb30
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008825"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout – metoda
Dokončí rozložení polí pro třídu, která byla definována před voláním [metody definetypedef –](imetadataemit-definetypedef-method.md).  
  
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
 pro `mdTypeDef`Token, který určuje třídu, která má být rozložena.  
  
 `dwPackSize`  
 pro Velikost balení: 1, 2, 4, 8 nebo 16 bajtů. Velikost balení je počet bajtů mezi sousedními poli.  
  
 `rFieldOffsets`  
 pro Pole struktur [COR_FIELD_OFFSET](cor-field-offset-structure.md) , z nichž každý určuje pole třídy a posun pole v rámci třídy. Pole ukončete pomocí `mdTokenNil` .  
  
 `ulClassSize`  
 pro Velikost třídy (v bajtech).  
  
## <a name="remarks"></a>Poznámky  
 Třída je zpočátku definována voláním metody [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md) a zadáním jednoho ze tří rozložení pro pole třídy: Automatic, sekvenční nebo Explicit. Normálně byste použili automatické rozložení a umožnili modulu runtime zvolit nejlepší způsob rozložení polí.  
  
 Můžete však chtít, aby pole byla rozložena podle uspořádání, které používá nespravovaný kód. V takovém případě vyberte buď sekvenční nebo explicitní rozložení, a volání `SetClassLayout` pro dokončení rozložení polí:  
  
- Sekvenční rozložení: Určete velikost balení. Pole je zarovnáno podle jeho přirozené velikosti nebo velikosti balení, podle toho, co je výsledkem menšího posunu pole. Nastavte `rFieldOffsets` a `ulClassSize` na nula.  
  
- Explicitní rozložení: buď zadejte posunutí jednotlivých polí, nebo zadejte velikost třídy a velikost balení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
