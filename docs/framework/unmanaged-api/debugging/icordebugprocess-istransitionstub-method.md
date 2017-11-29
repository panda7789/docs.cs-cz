---
title: "ICorDebugProcess::IsTransitionStub – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsTransitionStub
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 60f6e4116768d2d855edd941df796167754b3ab4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub – metoda
Získá hodnotu, která určuje, zda je adresa uvnitř se zakázaným inzerováním, které způsobí přechod do spravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [v] A `CORDB_ADDRESS` hodnotu, která určuje adresu nejistá.  
  
 `pbTransitionStub`  
 [out] Ukazatel na logickou hodnotu, která je `true` Pokud zadaná adresa je uvnitř se zakázaným inzerováním, které způsobí přechod do spravovaného kódu; v opačném případě *`pbTransitionStub` je `false`.  
  
## <a name="remarks"></a>Poznámky  
 `IsTransitionStub` Metoda lze pomocí nespravovaného kódu taktování při rozhodování, kdy se vraťte do spravovaných krokovač taktování ovládacího prvku.  
  
 Můžete také zástupných procedur přechod identity prohlížením informace do přenosného spustitelného souboru (PE).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
