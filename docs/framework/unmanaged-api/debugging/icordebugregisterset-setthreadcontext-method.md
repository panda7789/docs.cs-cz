---
title: "ICorDebugRegisterSet::SetThreadContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ac081cbd1fef0ca46750d8d7a74a22f23dbf0bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetsetthreadcontext-method"></a>ICorDebugRegisterSet::SetThreadContext – metoda
`SetThreadContext`v rozhraní .NET Framework verze 2.0 není implementováno. Tato metoda není volána.  
  
> [!NOTE]
>  Použijte vyšší úrovně operaci [icordebugnativeframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) nastavit kontext vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
