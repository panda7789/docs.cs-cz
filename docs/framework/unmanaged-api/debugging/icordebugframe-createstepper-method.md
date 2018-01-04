---
title: "ICorDebugFrame::CreateStepper – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f6741a030e72406fb8099c6373896d14cb9332
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframecreatestepper-method"></a>ICorDebugFrame::CreateStepper – metoda
Získá krokovač, které umožňuje provádět operace taktování relativně k této ICorDebugFrame ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppStepper`  
 [out] Ukazatel na adresu ICorDebugStepper objekt, který umožňuje ladicí program k provádění operací taktování vzhledem k aktuální snímek.  
  
## <a name="remarks"></a>Poznámky  
 Pokud rámečku není aktivní, objekt krokovač obvykle mají se vraťte do rámečku před dokončením kroku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
