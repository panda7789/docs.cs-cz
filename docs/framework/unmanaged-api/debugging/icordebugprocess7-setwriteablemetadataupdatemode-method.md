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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90136bd8a84cedebbfbb4848e763a1eaab293102
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533699"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>ICorDebugProcess7::SetWriteableMetadataUpdateMode – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Nakonfiguruje, zpracování v paměti aktualizace metadata v rámci cílového procesu ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) hodnota výčtu, která určuje, zda jsou viditelné v paměti aktualizace metadat v cílovém procesu (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) nebo nejsou viditelné (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) v ladicím programu.  
  
## <a name="remarks"></a>Poznámky  
 Aktualizace metadat cílového procesu můžou pocházet z funkce upravit a pokračovat, profiler, nebo <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugProcess7 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
