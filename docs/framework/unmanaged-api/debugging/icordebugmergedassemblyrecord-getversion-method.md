---
title: 'ICorDebugMergedAssemblyRecord:: GetVersion – metoda'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: cad71080c86e92beb318722db86011b09ce02e91
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207628"
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
 Informace o číslech verzí sestavení naleznete v <xref:System.Version> tématu třídy.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugMergedAssemblyRecord – rozhraní](icordebugmergedassemblyrecord-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
