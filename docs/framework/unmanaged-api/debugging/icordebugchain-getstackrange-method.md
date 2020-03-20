---
title: ICorDebugChain::GetStackRange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: 64e697323377d664b7b1e36bbf5931a44465cc51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178961"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange – metoda
Získá rozsah adres segmentu zásobníku pro tento řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStart`  
 [out] Ukazatel na `CORDB_ADDRESS` hodnotu, která je počáteční adresou segmentu zásobníku.  
  
 `pEnd`  
 [out] Ukazatel na `CORDB_ADDRESS` hodnotu, která je koncovou adresou segmentu zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Číselný rozsah je smysluplný pouze pro porovnání umístění rámců zásobníku. Nelze provádět žádné předpoklady o tom, co je skutečně uloženo v zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
