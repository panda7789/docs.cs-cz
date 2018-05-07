---
title: ICorDebugFrame::GetStackRange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5da87071bc23ac17a3077049cd77f0fb8611439f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange – metoda
Získá absolutní adresu rozsahu tento rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStart`  
 [out] Ukazatel `CORDB_ADDRESS` určující počáteční adresa rámce zásobníku reprezentována to `ICorDebugFrame` objektu.  
  
 `pEnd`  
 [out] Ukazatel `CORDB_ADDRESS` určující koncová adresa rámce zásobníku reprezentována to `ICorDebugFrame` objektu.  
  
## <a name="remarks"></a>Poznámky  
 Rozsah adres v zásobníku je užitečné pro piecing společně trasování prokládaná zásobníku získané z více ladění webů. Číselný rozsah poskytuje žádné informace o obsahu rámce zásobníku. Je smysl jenom pro porovnání umístění rámce zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
