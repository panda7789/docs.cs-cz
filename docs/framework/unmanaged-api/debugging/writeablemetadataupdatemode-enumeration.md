---
title: Výčet WriteableMetadataUpdateMode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fbf9a24c350dd4c33bb50b0add8817c8922925f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="writeablemetadataupdatemode-enumeration"></a>Výčet WriteableMetadataUpdateMode
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Obsahuje hodnoty, které určují, zda jsou viditelné pro ladicí program aktualizace v paměti pro metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a>Členové  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|Zachování kompatibility s předchozími verzemi rozhraní .NET Framework při provádění aktualizací v paměti metadata viditelné. Další informace naleznete v části Poznámky.|  
|`AlwaysShowUpdates`|Zpřístupněte aktualizace v paměti k metadatům pro ladicí program.|  
  
## <a name="remarks"></a>Poznámky  
 Člen `WriteableMetadataUpdateMode` výčtu se dá předat do [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) metoda řídit, jestli v paměti aktualizace metadat v tento cílový proces jsou viditelné pro ladicí program.  
  
 `LegacyCompatPolicy` Možnost vynucuje stejné chování jako verze rozhraní .NET Framework před 4.5.2. Často to znamená, že metadata z webu aktualizace od není viditelná. Volání metody, ladění ale coerce implicitně ladicí program ke zviditelnění aktualizace. Například v případě úspěšného ladicího programu [icordebugilframe::getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) index proměnné nebyla nalezena v metody původní metadata, všechna metadata pro modul se aktualizuje na snímku odpovídající aktuální stav proces. Jinými slovy, pomocí `LegacyCompatPolicy` možnost ladicího programu setkat none, některé nebo všechny aktualizace k dispozici metadata, v závislosti na tom, jak ji používá dalších částí nespravovaného rozhraní API pro ladění.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [SetWriteableMetadataUpdateMode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
