---
title: 'ICorDebugMergedAssemblyRecord:: getssdp – metoda'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 21e8ebeabd3b082361ca3307240cfca58835b066
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793085"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a>ICorDebugMergedAssemblyRecord:: getssdp – metoda
Získá jednoduchý název sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 pro Počet znaků ve vyrovnávací paměti `szName`.  
  
 `pcchName`  
 mimo Ukazatel na počet znaků skutečně zapsaných do vyrovnávací paměti `szName`.  
  
 `szName`  
 Ukazatel na pole znaků.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte jednoduchý název sestavení (například System. Collections) bez přípony souboru, verze, jazykové verze nebo tokenu veřejného klíče. Odpovídá vlastnosti <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> ve spravovaném kódu.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMergedAssemblyRecord – rozhraní](icordebugmergedassemblyrecord-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
