---
title: ICorConfiguration::AddDebuggerSpecialThread – metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db1b19c1499f7e8a126933b4d0635a0ab73e72a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218586"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a>ICorConfiguration::AddDebuggerSpecialThread – metoda
Ladění služeb označuje, že konkrétní vlákno by měla být povolena má pokračovat provedením zatímco ladicí program zastavuje během scénáře ladění spravované nebo nespravované aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwSpecialThreadId`  
 [in] ID vlákna, která by měla bude moct pokračovat v provádění.  
  
## <a name="remarks"></a>Poznámky  
 Zadané vlákno nebude moci spouštět spravovaný kód nebo zadejte modul runtime žádným způsobem. Příkladem takových vlákno může být vlákno v procesu pro podporu ladicí programy starší verzi skriptu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorConfiguration – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
