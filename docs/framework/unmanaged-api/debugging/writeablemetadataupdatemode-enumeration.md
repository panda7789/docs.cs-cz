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
ms.openlocfilehash: 0793dcbe4d080da83cf507e04303d66fbbb56b85
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420640"
---
# <a name="writeablemetadataupdatemode-enumeration"></a>Výčet WriteableMetadataUpdateMode
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Poskytuje hodnoty, které určují, zda mají být aktualizace metadat v paměti viditelné ladicímu programu.  
  
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
|`LegacyCompatPolicy`|Zachovat kompatibilitu s předchozími verzemi .NET Framework při zpřístupnění aktualizací v paměti na metadatech Další informace naleznete v části Poznámky.|  
|`AlwaysShowUpdates`|Zpřístupnit v paměti aktualizace metadat viditelných pro ladicí program.|  
  
## <a name="remarks"></a>Poznámky  
 Člen `WriteableMetadataUpdateMode` výčtu může být předán metodě [SetWriteableMetadataUpdateMode –](icordebugprocess7-setwriteablemetadataupdatemode-method.md) , která určuje, zda jsou aktualizace v paměti metadat v cílovém procesu viditelné ladicímu programu.  
  
 `LegacyCompatPolicy`Možnost vynutila stejné chování jako ve verzích .NET Framework před 4.5.2. To často znamená, že metadata z aktualizací nejsou viditelná. Nicméně volání na řadu metod ladění implicitně převede ladicí program, aby byly aktualizace viditelné. Například pokud ladicí program projde [ICorDebugILFrame:: GetLocalVariable –](icordebugilframe-getlocalvariable-method.md) index proměnné, který nebyl nalezen v původních metadatech metody, všechna metadata pro modul jsou aktualizována na snímek, který odpovídá aktuálnímu stavu procesu. Jinými slovy, `LegacyCompatPolicy` ladicí program se může v závislosti na tom, jak používá jiné části nespravovaného rozhraní API pro ladění, zobrazit žádné, některé nebo všechny dostupné aktualizace metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Ladění výčtů](debugging-enumerations.md)
- [SetWriteableMetadataUpdateMode – metoda](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
