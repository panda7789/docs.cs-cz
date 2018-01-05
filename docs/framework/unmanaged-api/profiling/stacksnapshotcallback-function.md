---
title: "StackSnapshotCallback – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackSnapshotCallback
api_location: mscorwks.dll
api_type: COM
f1_keywords: StackSnapshotCallback
helpviewer_keywords: StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32cf21fb5a76fdec4daa322d53a8eb218ae2f2b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback – funkce
Poskytuje informace o každé spravované rámečkem a každé spuštění nespravované rámce v zásobníku při procházení zásobníku, který je inicializován nástrojem profileru [ICorProfilerInfo2::dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [v] Pokud je tato hodnota nulová, je tato zpětné volání pro spouštění funkce nespravované rámce; jinak je identifikátor spravované funkce a je tento zpětné volání pro spravované rámce.  
  
 `ip`  
 [v] Hodnota ukazatel instrukce nativního kódu v rámečku.  
  
 `frameInfo`  
 [v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku. Tato hodnota je platná pouze během této zpětného volání.  
  
 `contextSize`  
 [v] Velikost `CONTEXT` strukturu, která odkazuje `context` parametr.  
  
 `context`  
 [v] Ukazatel na Win32 `CONTEXT` struktura, která představuje stav procesoru pro tento snímek.  
  
 `context` Parametr je platný pouze v případě, že byla předána příznak COR_PRF_SNAPSHOT_CONTEXT `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 [v] Ukazatel na klienta data, která je předána přímo z `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Poznámky  
 `StackSnapshotCallback` Funkce je implementována pro zápis profileru. Je nutné omezit složitosti práci `StackSnapshotCallback`. Například při použití `ICorProfilerInfo2::DoStackSnapshot` v asynchronním režimu, může být cílový vlákno podržíte zámky. Pokud kódu v rámci `StackSnapshotCallback` vyžaduje stejné zámků, by mohly vzájemné zablokování.  
  
 `ICorProfilerInfo2::DoStackSnapshot` Volání metod `StackSnapshotCallback` funkce jednou za spravované snímek nebo jednou za spuštění nespravované rámce. Pokud `StackSnapshotCallback` je volána pro běh nespravované rámce, může použít profileru kontext registrace (odkazuje `context` parametr) k provedení vlastní procházení nespravované zásobníku. V tomto případě Win32 `CONTEXT` struktura představuje stav procesoru pro nedávno stisknutí rámečku v rámci spustit nespravované snímků. I když Win32 `CONTEXT` struktura zahrnuje hodnoty pro všechny registrů, spoléhat na hodnoty registru ukazatel zásobníku, rámec ukazatel registru, registrace ukazatel instrukce a permanentní (ke které se zachovají) zaregistruje celé číslo.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [DoStackSnapshot – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
