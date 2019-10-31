---
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
ms.openlocfilehash: 453486c9e3d98ffd6f0dcfa08e7a0a9a1c1d3342
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123392"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>ICorDebugProcess7::SetWriteableMetadataUpdateMode – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Konfiguruje, jak ladicí program zpracovává aktualizace v paměti na metadata v rámci cílového procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 Hodnota výčtu [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) , která určuje, zda jsou aktualizace metadat v paměti v cílovém procesu viditelné (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) nebo nejsou viditelné (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) do ladicího programu.  
  
## <a name="remarks"></a>Poznámky  
 Aktualizace metadat cílového procesu můžou pocházet z části Upravit a pokračovat, profileru nebo <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess7 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
