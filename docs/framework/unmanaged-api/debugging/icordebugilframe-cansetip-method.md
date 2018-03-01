---
title: "ICorDebugILFrame::CanSetIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 22d0df9add0a4ce35b1a590d65e30a6756fec49c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP – metoda
Získá HRESULT určující, zda je možné nastavit ukazatel instrukce do zadaného umístění posunu v kódu Microsoft Intermediate Language (MSIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nOffset`  
 [v] Ukazatel instrukce požadované nastavení.  
  
## <a name="remarks"></a>Poznámky  
 Použití `CanSetIP` metoda před voláním [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) metoda. Pokud `CanSetIP` vrátí všechny HRESULT než S_OK, můžete stále vyvolat `ICorDebugILFrame::SetIP`, ale neexistuje žádná záruka, že bezpečné a správné spuštění kódu laděné bude pokračovat, ladicího programu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug, h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
