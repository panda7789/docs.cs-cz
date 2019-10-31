---
title: 'ICorDebugMergedAssemblyRecord:: GetVersion – metoda'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 0c89d0749281da412bbf71400d51bee1ed651fbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129772"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>ICorDebugMergedAssemblyRecord:: GetVersion – metoda
Získá informace o verzi sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pMajor`  
 mimo Ukazatel na hlavní číslo verze.  
  
 `pMinor`  
 mimo Ukazatel na číslo dílčí verze.  
  
 `pBuild`  
 mimo Ukazatel na číslo buildu.  
  
 `pRevision`  
 mimo Ukazatel na číslo revize.  
  
## <a name="remarks"></a>Poznámky  
 Informace o číslech verzí sestavení naleznete v tématu <xref:System.Version> třídy.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMergedAssemblyRecord – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
