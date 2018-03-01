---
title: "ICorProfilerCallback::Shutdown – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 42c9abc3c255f7ddda5e7934c495b073a7b1f6fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown – metoda
Aby se aplikace vypíná upozorní profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Poznámky  
 Kód profileru nelze bezpečně volat metody [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) rozhraní po `Shutdown` metoda je volána. Volání `ICorProfilerInfo` metody za následek nedefinované chování po `Shutdown` metoda vrátí. Určité neměnné události může stále dojít po vypnutí; vrátit okamžitě v takovém případě by měl postará profileru.  
  
 `Shutdown` Volání metody pouze v případě, že spravované aplikace, která je vytvořený profil spustit jako spravovaného kódu (to znamená, je spravován na počáteční rámce v zásobníku proces). Pokud aplikace spustit jako nespravovaný kód, ale později přešli do spravovaného kódu, čímž vytvoření instance common language runtime (CLR), pak `Shutdown` nebude volána. Pro tyto případy by měla obsahovat profileru své knihovny `DllMain` rutiny, která používá DLL_PROCESS_DETACH hodnotu uvolněte všechny prostředky a provést čištění zpracování svá data, jako je například, abyste vyprázdnili trasování na disk a tak dále.  
  
 Obecně platí musí profileru zvládl neočekávané vypnutí systému. Například může být proces byl zastaven na Win32 `TerminateProcess` – metoda (deklarované v Winbase.h). V ostatních případech se modulu CLR zastaví určité spravovaných vláknech (vlákna na pozadí) bez doručování zpráv řádné odstraňování pro ně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Initialize – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
