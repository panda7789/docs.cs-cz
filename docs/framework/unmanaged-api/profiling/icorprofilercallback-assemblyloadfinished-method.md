---
title: ICorProfilerCallback::AssemblyLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bb5586271c252879b503dd093c88380197d5bce
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479724"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a>ICorProfilerCallback::AssemblyLoadFinished – metoda
Oznámí profileru, že sestavení bylo dokončeno načítání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `assemblyId`  
 [in] Určuje sestavení, který byl načten.  
  
 `hrStatus`  
 [in] HRESULT, která určuje, zda sestavení bylo dokončeno načítání úspěšně.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `assemblyId` není platná pro požadavek informace do `AssemblyLoadFinished` metoda je volána.  
  
 Některé části načítání sestavení může pokračovat po `AssemblyLoadFinished` zpětného volání. Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu. Ale úspěch HRESULT v `hrStatus` značí pouze, že první část načítání sestavení byla úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
