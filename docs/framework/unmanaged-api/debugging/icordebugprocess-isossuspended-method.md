---
title: ICorDebugProcess::IsOSSuspended – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b65a621541f2b4a800f6b3708a6b257374c5866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
