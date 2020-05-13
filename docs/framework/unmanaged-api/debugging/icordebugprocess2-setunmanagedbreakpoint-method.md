---
title: ICorDebugProcess2::SetUnmanagedBreakpoint – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: 6b9396d03892f29e3698af90856d0c0023dc628a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213462"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint – metoda
Nastaví nespravovanou zarážku na zadaném posunu nativní bitové kopie.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 pro `CORDB_ADDRESS`Objekt, který určuje posunutí nativní bitové kopie.  
  
 `bufsize`  
 pro Velikost pole v bajtech `buffer` .  
  
 `buffer`  
 mimo Pole, které obsahuje operační kód, který je nahrazen zarážkou.  
  
 `bufLen`  
 mimo Ukazatel na počet bajtů vrácených v `buffer` poli.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je posun nativní bitové kopie v rámci modulu CLR (Common Language Runtime), zarážka bude ignorována. To umožňuje modulu CLR zabránit odesílání zarážek mimo pásmo, pokud je zarážka nastavena v ladicím programu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
