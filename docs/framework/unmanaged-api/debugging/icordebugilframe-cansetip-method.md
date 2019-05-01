---
title: ICorDebugILFrame::CanSetIP – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49cef22e88613fe4c4dfb3fb35a92977977b1827
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988634"
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP – metoda
Získá HRESULT, která určuje, jestli je bezpečný pro nastavení ukazatele na instrukci do zadaného umístění posunu v kódu Microsoft Intermediate Language (MSIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 [in] Požadované nastavení pro ukazatele na instrukci.  
  
## <a name="remarks"></a>Poznámky  
 Použití `CanSetIP` před voláním metody [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) metody. Pokud `CanSetIP` vrátí všechny HRESULT než S_OK, můžete stále vyvolat `ICorDebugILFrame::SetIP`, ale neexistuje žádná záruka, že ladicí program bude pokračovat v provádění bezpečné a správné kódu, který se právě ladí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** H CorDebug.idl, CorDebug,  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
