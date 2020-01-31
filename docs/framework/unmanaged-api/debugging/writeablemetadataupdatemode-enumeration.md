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
ms.openlocfilehash: 5c3f2f7a9c0804b71c9c8a52bb032aca7c03825e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790296"
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
 Člen výčtu `WriteableMetadataUpdateMode` lze předat metodě [SetWriteableMetadataUpdateMode –](icordebugprocess7-setwriteablemetadataupdatemode-method.md) a určit tak, zda mají být aktualizace v paměti metadaty v cílovém procesu viditelné ladicímu programu.  
  
 Možnost `LegacyCompatPolicy` vynutila stejné chování jako ve verzích .NET Framework před 4.5.2. To často znamená, že metadata z aktualizací nejsou viditelná. Nicméně volání na řadu metod ladění implicitně převede ladicí program, aby byly aktualizace viditelné. Například pokud ladicí program projde [ICorDebugILFrame:: GetLocalVariable –](icordebugilframe-getlocalvariable-method.md) index proměnné, který nebyl nalezen v původních metadatech metody, všechna metadata pro modul jsou aktualizována na snímek, který odpovídá aktuálnímu stavu procesu. Jinými slovy, s možností `LegacyCompatPolicy`, ladicí program se může v závislosti na tom, jak používá jiné části nespravovaného rozhraní API pro ladění, zobrazovat žádná, některá nebo všechna dostupná aktualizace metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](debugging-enumerations.md)
- [SetWriteableMetadataUpdateMode – metoda](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
