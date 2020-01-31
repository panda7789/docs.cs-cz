---
title: ICorDebugSymbolProvider2 – rozhraní
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
ms.openlocfilehash: ca5bb822be515c936560eb4888c72ea306888ff3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791491"
---
# <a name="icordebugsymbolprovider2-interface"></a>ICorDebugSymbolProvider2 – rozhraní
Logicky rozšiřuje rozhraní [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) a načítá Další informace o symbolech ladění.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetFrameProps – metoda](icordebugsymbolprovider2-getframeprops-method.md)|Vrátí metodu, která spouští relativní virtuální adresu metody a nadřazený rámec pro relativní virtuální adresu kódu.|  
|[GetGenericDictionaryInfo – metoda](icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|Načte mapu obecného slovníku.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugSymbolProvider – rozhraní](icordebugsymbolprovider-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
