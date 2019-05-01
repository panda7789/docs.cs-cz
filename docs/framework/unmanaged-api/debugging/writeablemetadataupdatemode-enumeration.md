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
ms.openlocfilehash: 62e4328b75a7f6fecc28cd620ec3ac18460316c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993444"
---
# <a name="writeablemetadataupdatemode-enumeration"></a>Výčet WriteableMetadataUpdateMode
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Obsahuje hodnoty, které určují, jestli jsou viditelné pro ladicí program v paměti aktualizace metadat.  
  
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
|`LegacyCompatPolicy`|Zachování kompatibility s předchozími verzemi rozhraní .NET Framework při provádění aktualizací v paměti k metadatům viditelné. Další informace naleznete v části Poznámky.|  
|`AlwaysShowUpdates`|Zviditelnit v paměti aktualizace metadat k ladicímu programu.|  
  
## <a name="remarks"></a>Poznámky  
 Člen `WriteableMetadataUpdateMode` výčet může být předán [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) metoda řídit, jestli v paměti aktualizace metadat v cílovém procesu jsou viditelné pro ladicí program.  
  
 `LegacyCompatPolicy` Možnost vynucuje stejné chování jako verze rozhraní .NET Framework před 4.5.2. To často znamená, že metadata z webu aktualizace od není viditelný. Volání na počet ladění metody však implicitně převedeno ladicí program ke zviditelnění aktualizace. Například, pokud ladicí program projde [icordebugilframe::getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) index proměnná se nenašla v metadatech původní metody, všechna metadata modulu je aktualizovaná na snímek aktuálního stavu odpovídajících proces. Jinými slovy, se `LegacyCompatPolicy` možnost, ladicí program může zobrazit, none, některé nebo všechny aktualizace metadat k dispozici, v závislosti na tom, jak používá jiné části nespravované ladění rozhraní API.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [SetWriteableMetadataUpdateMode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
