---
title: ICorProfilerCallback::ExceptionCLRCatcherFound – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59225677671388b4ed31f7fa440b6e502b604c63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073011"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a>ICorProfilerCallback::ExceptionCLRCatcherFound – metoda
Voláno, když `catch` block pro výjimku se nachází uvnitř common language runtime (CLR), samotného. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.0  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ExceptionCLRCatcherExecute – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
