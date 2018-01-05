---
title: "ICorProfilerCallback::JITInlining – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITInlining
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3990fdf1bcf76592288aac35b47b15f42cf77bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining – metoda
Upozorní profileru, že kompilátoru v běhu (JIT) se chystáte vložit funkci souladu jinou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a>Parametry  
 `callerId`  
 [v] ID funkce, do kterého `calleeId` funkce bude možné vložit.  
  
 `calleeId`  
 [v] ID funkce má být vložen.  
  
 `pfShouldInline`  
 [out] `true` vkládání dojít, jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 Můžete nastavit profileru `pfShouldInline` k `false` zabránit `calleeId` funkce z vkládání do `callerId` funkce. Navíc můžete profileru globálně zakázat vložené vložení pomocí COR_PRF_DISABLE_INLINING hodnotu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.  
  
 Vložené funkce Vložit není vyvolávání událostí pro zadání nebo ponechat. Proto musíte nastavit profileru `pfShouldInline` k `false` Chcete-li vytvořit přesný callgraph. Nastavení `pfShouldInline` k `false` ovlivní výkon, protože vložené vložení obvykle zvyšuje rychlost a snižuje počet samostatné událostí JIT kompilace pro metodu vložené.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
