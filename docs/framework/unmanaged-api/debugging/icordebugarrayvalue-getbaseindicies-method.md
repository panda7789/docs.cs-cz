---
title: ICorDebugArrayValue::GetBaseIndicies – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3fe9edf7a635e54aac881a242aca3bc32e21fe1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408122"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a>ICorDebugArrayValue::GetBaseIndicies – metoda
Získá základní index Každá dimenze v poli.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cdim`  
 [v] Počet dimenzí tohoto `ICorDebugArrayValue` objektu. Tato hodnota je také velikost `indicies` pole, protože jeho velikost se rovná počet rozměrů `ICorDebugArrayValue` objektu.  
  
 `indicies`  
 [out] Pole celých čísel, z nichž každý je základní index (to znamená, počáteční index) dimenze tohoto `ICorDebugArrayValue` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
