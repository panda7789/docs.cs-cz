---
title: ICorDebugModule::GetName – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ae9bc5925634f8bba71731a0c51eb19cf9eec04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663950"
---
# <a name="icordebugmodulegetname-method"></a>ICorDebugModule::GetName – metoda
Získá název souboru modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchname`  
 [in] Velikost `szName` pole.  
  
 `pcchName`  
 [in] Ukazatel na vrácený název.  
  
 `szName`  
 [out] Pole, která ukládá vrácený název.  
  
## <a name="remarks"></a>Poznámky  
 `GetName` Metoda vrátí hodnotu S_OK HRESULT, pokud název souboru modulu odpovídá názvu na disku. `GetName` Vrátí S_FALSE HRESULT, pokud je název kovodělných, například pro modul dynamické nebo v paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:


