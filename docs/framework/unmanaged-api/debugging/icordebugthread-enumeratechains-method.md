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
ms.openlocfilehash: 711fccd65379bc3e5e178869e7220dd84fd07fbe
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379706"
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
 mimo Ukazatel na adresu `ICorDebugChainEnum` objektu, který umožňuje vyčíslení všech řetězů zásobníku v tomto vlákně počínaje aktivním řetězcem (to znamená nejnovější).  
  
## <a name="remarks"></a>Poznámky  
 Řetěz zásobníku představuje fyzický zásobník volání pro vlákno. V následujících případech se vytvoří hranice řetězu zásobníku:  
  
- Přechod z spravovaného do nespravovaného nebo nespravovaného na nespravovaný.  
  
- Kontextový přepínač.  
  
- Napadení ladicího programu v uživatelském vlákně.  
  
 V jednoduchém případě pro vlákno, které spouští čistě spravovaný kód v jednom kontextu, bude existovat korespondence 1:1 mezi vlákny a řetězy zásobníku.  
  
 Ladicí program může chtít změnit uspořádání fyzických zásobníků volání všech vláken do logických zásobníků volání. To by mělo zahrnovat řazení všech zřetězení vláken podle jejich vztahů volající/volaný a jejich přeseskupování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
