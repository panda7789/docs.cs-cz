---
title: ICorDebugStackWalk::GetContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 743b0c8016ca5c0401046166a770d857215429a3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379217"
---
# <a name="icordebugstackwalkgetcontext-method"></a>ICorDebugStackWalk::GetContext – metoda
Vrátí kontext pro aktuální rámec v objektu [ICorDebugStackWalk](icordebugstackwalk-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `contextFlags`  
 pro Příznaky, které označují požadovaný obsah vyrovnávací paměti kontextu (definované v souboru WinNT. h).  
  
 `contextBufSize`  
 pro Přidělená velikost vyrovnávací paměti kontextu.  
  
 `contextSize`  
 mimo Skutečná velikost kontextu. Tato hodnota musí být menší nebo rovna velikosti vyrovnávací paměti kontextu.  
  
 `contextBuf`  
 mimo Vyrovnávací paměť kontextu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Kontext pro aktuální rámec byl úspěšně vrácen.|  
|E_FAIL|Kontext nelze vrátit.|  
|HRESULT_FROM_WIN32 (VYROVNÁVACÍ PAMĚŤ ERROR_INSUFFICIENT)|Kontextová vyrovnávací paměť je příliš malá.|  
|CORDBG_E_PAST_END_OF_STACK|Ukazatel na rámec je již na konci zásobníku; Proto nelze mít k dispozici žádné další snímky.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že unwinda obnoví pouze podmnožinu registrů, například nestálé Registry, kontext nemusí přesně odpovídat stavu registrace v době volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
