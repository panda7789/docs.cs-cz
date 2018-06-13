---
title: ICorDebugProcess::GetHelperThreadID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c3f879e04a710d65f812a5165c3edbfa31f8542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419065"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID – metoda
Získá ID vlákna operační systém (OS) ladicího programu interní pomocná přístup z více vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThreadID`  
 [out] Ukazatel na operačního systému thread ID vlákna interní pomocná ladicího programu.  
  
## <a name="remarks"></a>Poznámky  
 Během ladění spravovanými a nespravovanými, je odpovědností ladicího programu zajistit, že vlákno se zadaným ID zůstane spuštěný, pokud volání zarážku umístěna pomocí ladicího programu. Ladicí program také chtít skrýt tohoto podprocesu od uživatele. Pokud existuje žádné pomocná přístup z více vláken v procesu ještě `GetHelperThreadID` metoda vrátí hodnotu nula v *`pThreadID`.  
  
 ID vlákna vlákno pomocné rutiny, nelze mezipaměti, protože můžou časem změnit. ID vlákna v každé události zastavení musí znovu zadat dotaz.  
  
 ID vlákna vlákno pomocná ladicího programu bude správné na každý nespravované [icordebugmanagedcallback::CreateThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) událostí, což umožňuje ladicí program určete ID vlákna jeho pomocné rutiny přístup z více vláken a skrýt od uživatele. Podproces, který je označený pomocná vlákno během nespravované `ICorDebugManagedCallback::CreateThread` událostí nikdy spustí kód spravované uživatele.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl. CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
