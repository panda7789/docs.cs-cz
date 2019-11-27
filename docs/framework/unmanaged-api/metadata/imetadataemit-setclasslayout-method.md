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
ms.openlocfilehash: 5214298c6ad9594548ab45ed583cb5b14ce1f30d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441762"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout – metoda
Dokončí rozložení polí pro třídu, která byla definována před voláním [metody definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
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
 pro Token `mdTypeDef`, který určuje třídu, která má být rozložena.  
  
 `dwPackSize`  
 pro Velikost balení: 1, 2, 4, 8 nebo 16 bajtů. Velikost balení je počet bajtů mezi sousedními poli.  
  
 `rFieldOffsets`  
 pro Pole struktur [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) , z nichž každý určuje pole třídy a posun pole v rámci třídy. Ukončete pole pomocí `mdTokenNil`.  
  
 `ulClassSize`  
 pro Velikost třídy (v bajtech).  
  
## <a name="remarks"></a>Poznámky  
 Třída je zpočátku definována voláním metody [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) a zadáním jednoho ze tří rozložení pro pole třídy: Automatic, sekvenční nebo Explicit. Normálně byste použili automatické rozložení a umožnili modulu runtime zvolit nejlepší způsob rozložení polí.  
  
 Můžete však chtít, aby pole byla rozložena podle uspořádání, které používá nespravovaný kód. V takovém případě vyberte buď sekvenční nebo explicitní rozložení, a volání `SetClassLayout` pro dokončení rozložení polí:  
  
- Sekvenční rozložení: Určete velikost balení. Pole je zarovnáno podle jeho přirozené velikosti nebo velikosti balení, podle toho, co je výsledkem menšího posunu pole. Nastavte `rFieldOffsets` a `ulClassSize` na nulu.  
  
- Explicitní rozložení: buď zadejte posunutí jednotlivých polí, nebo zadejte velikost třídy a velikost balení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
