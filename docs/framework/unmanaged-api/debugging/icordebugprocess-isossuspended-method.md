---
title: "ICorDebugProcess::IsOSSuspended – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsOSSuspended
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 140855ca2828ba2a8fdf811d29fc512f6ccd20e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended – metoda
Získá hodnotu, která určuje zadaný vlákno pozastavila v důsledku ladicí program ukončení tohoto procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [v] ID dotyčném pro přístup z více vláken.  
  
 `pbSuspended`  
 [out] Ukazatel na logickou hodnotu, která je `true` Pokud zadané vlákno byl pozastavený; jinak hodnota *`pbSuspended` je `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud v důsledku ladicí program ukončení tohoto procesu se pozastavilo zadaný vlákno, zadaný vlákno Win32 pozastavit počet zvýší o jednu. Ladicí program uživatelské rozhraní (UI) chtít provést tyto informace do účtu, pokud se zobrazí operační systém (OS) pozastavit počet vlákno pro uživatele.  
  
 `IsOSSuspended` Metoda má smysl pouze v kontextu nespravované ladění. Během spravované ladění vláken jsou spolupráce při pozastavenou spíše než pozastaveno operačního systému.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
