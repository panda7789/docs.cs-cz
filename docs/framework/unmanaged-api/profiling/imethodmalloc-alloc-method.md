---
title: IMethodMalloc::Alloc – metoda
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: af881d23ff77f05dadbbc745b973979e35ebe9f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447565"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc – metoda

Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.

## <a name="syntax"></a>Syntaxe

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>Parametry

`cb`\
[in] The number of bytes to allocate for the method body.

## <a name="remarks"></a>Poznámky

 The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator. In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address. If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.

 The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.

## <a name="requirements"></a>Požadavky
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).

 **Header:** CorProf.idl, CorProf.h

 **Library:** CorGuids.lib

 **.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [IMethodMalloc – rozhraní](imethodmalloc-interface.md)
