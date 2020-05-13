---
title: Rozhraní ICorDebugILFrame4
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: d0b1c31d45efea4892182c43c801112530361994
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213699"
---
# <a name="icordebugilframe4-interface"></a>Rozhraní ICorDebugILFrame4
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Poskytuje metody, které umožňují přístup k místním proměnným a kódu v bloku rozhraní IL (Intermediate Language). Parametr určuje, jestli má ladicí program přístup k proměnným a kódu přidanému v profileru ReJIT instrumentace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx – metoda](icordebugilframe4-enumeratelocalvariablesex-method.md)|Vrátí seznam místních proměnných dostupných v aktuálním rámci.|  
|[GetCodeEx – metoda](icordebugilframe4-getcodeex-method.md)|Vrátí kód, na kterém je spuštěn tento rámec zásobníku.|  
|[GetLocalVariableEx – metoda](icordebugilframe4-getlocalvariableex-method.md)|Vrátí hodnotu lokální proměnné v rámci rámce IL.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto metody nabízejí funkce kromě těch, které poskytují metody [EnumerateLocalVariables –](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)a [GetLocalVariable –](icordebugilframe-getlocalvariable-method.md) . Každá metoda zahrnuje `flags` parametr, který určuje, zda jsou viditelné další lokální proměnné nebo kód definované žádostí ReJIT profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
