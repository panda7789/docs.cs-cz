---
title: ICorDebugThread::EnumerateChains – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
ms.openlocfilehash: 38fe50f5a6608bb27d7a7818dee4784a7f8113ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133610"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains – metoda
Získá ukazatel rozhraní na enumerátor ICorDebugChainEnum, který obsahuje všechny řetězy zásobníku v tomto objektu ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppChains`  
 mimo Ukazatel na adresu `ICorDebugChainEnum` objektu, který umožňuje vyčíslení všech řetězů zásobníku v tomto vlákně počínaje aktivním řetězcem (to znamená nejnovější) řetěz.  
  
## <a name="remarks"></a>Poznámky  
 Řetěz zásobníku představuje fyzický zásobník volání pro vlákno. V následujících případech se vytvoří hranice řetězu zásobníku:  
  
- Přechod z spravovaného do nespravovaného nebo nespravovaného na nespravovaný.  
  
- Kontextový přepínač.  
  
- Napadení ladicího programu v uživatelském vlákně.  
  
 V jednoduchém případě pro vlákno, které spouští čistě spravovaný kód v jednom kontextu, bude existovat korespondence 1:1 mezi vlákny a řetězy zásobníku.  
  
 Ladicí program může chtít změnit uspořádání fyzických zásobníků volání všech vláken do logických zásobníků volání. To by mělo zahrnovat řazení všech zřetězení vláken podle jejich vztahů volající/volaný a jejich přeseskupování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
