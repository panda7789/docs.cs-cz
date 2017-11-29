---
title: "ICorDebugThread::EnumerateChains – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.EnumerateChains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67b5a5da0a0053536ab4331e9d134464a4330500
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains – metoda
Získá ukazatele rozhraní na enumerátor ICorDebugChainEnum, který obsahuje všechny řetězy zásobníku v tomto objektu ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppChains`  
 [out] Ukazatel na adresu `ICorDebugChainEnum` objekt, který umožňuje výčet všech zásobníku zřetězený v tohoto podprocesu počínaje řetězu aktivní (tedy nejnovější).  
  
## <a name="remarks"></a>Poznámky  
 Řetězu zásobník představuje zásobníku volání fyzické pro vlákno. V těchto případech vytvoření hranice řetězu zásobníku:  
  
-   Spravované na nespravované nebo nespravovaného do spravovaného přechod.  
  
-   Kontext přepínač.  
  
-   A zneužití uživatelské vlákno ladicího programu.  
  
 V případě jednoduchého pro vlákno, které běží v kontextu jedné čistě spravovaného kódu, budou existovat souvislosti mezi vláken a řetězy zásobníku.  
  
 Ladicí program chtít Změna uspořádání zásobníky volání fyzické všechny podprocesy do zásobníky logické volání. To by zahrnovat všechny vláken řetězy řazení podle jejich volající/volaný vztahů a přerozdělit je.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
