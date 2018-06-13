---
title: ICorDebugController::Detach – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cad8b305de580ce7cf4876939b95cc05d0fd11f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411480"
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach – metoda
Umožňuje odpojit ladicí program z domény procesů nebo aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Domény procesů nebo aplikace pokračuje provádění za normálních okolností, ale objekt "ICorDebugProcess" nebo "ICorDebugAppDomain" již není platný a dojde k žádné další zpětných volání.  
  
 V rozhraní .NET Framework verze 2.0 Pokud je povoleno ladění nespravované, tato metoda selže z důvodu omezení operačního systému.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
