---
title: ICorProfilerCallback::JITInlining – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 13ce44c9c7a04b870278bc8926dd9fe5daf10bc3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500010"
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining – metoda
Upozorní profileru, že kompilátor JIT (just-in-time) se chystá Vložit funkci do řádku s jinou funkcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>Parametry  
 `callerId`  
 pro ID funkce, do které `calleeId` bude vložena funkce  
  
 `calleeId`  
 pro ID funkce, která má být vložena.  
  
 `pfShouldInline`  
 [out] `true` aby bylo možné vložení provést; v opačném případě `false` .  
  
## <a name="remarks"></a>Poznámky  
 Profiler může nastavit, `pfShouldInline` aby `false` zabránil `calleeId` Vložení funkce do `callerId` funkce. Profiler může také globálně zakázat vložené vložení pomocí COR_PRF_DISABLE_INLINING hodnoty výčtu [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .  
  
 Funkce vložené vložením nevyvolávají události pro vložení nebo ukončení. Proto musí Profiler nastavit na, `pfShouldInline` aby `false` vytvořil přesný graf volání. Nastavení `pfShouldInline` na `false` bude mít vliv na výkon, protože vložené vložení obvykle zvyšuje rychlost a snižuje počet samostatných událostí kompilace JIT pro vloženou metodu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
