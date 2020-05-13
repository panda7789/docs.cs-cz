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
ms.openlocfilehash: 6de75e1e27660ac91bd6320a501db47f3b055fb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212253"
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
 Hodnota výčtu [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) , která určuje, zda jsou aktualizace v paměti metadaty v cílovém procesu viditelné ( `WriteableMetadataUpdateMode::AlwaysShowUpdates` ) nebo nejsou viditelné ( `WriteableMetadataUpdateMode::LegacyCompatPolicy` ) do ladicího programu.  
  
## <a name="remarks"></a>Poznámky  
 Aktualizace metadat cílového procesu můžou pocházet z části Upravit a pokračovat, profileru nebo <xref:System.Reflection.Emit?displayProperty=nameWithType> .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugProcess7](icordebugprocess7-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
