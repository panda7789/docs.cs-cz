---
title: ICorProfilerFunctionControl::SetILFunctionBody – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: a6b24fd59a183a4a59b117663772417d55cc67db
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503134"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a>ICorProfilerFunctionControl::SetILFunctionBody – metoda
Nahrazuje tělo Common Intermediate Language (CIL) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbNewILMethodHeader`  
 [in] Celková velikost nového CIL, včetně hlavičky a všech struktur za tělem.  
  
 `pbNewILMethodHeader`  
 [in] Ukazatel na novou hlavičku CIL.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Nahrazení proběhlo úspěšně.|  
  
## <a name="remarks"></a>Poznámky  
 Na rozdíl od metody [ICorProfilerInfo:: SetILFunctionBody –](icorprofilerinfo-setilfunctionbody-method.md) `SetILFunctionBody` spravuje metoda paměť potřebnou pro nový tělo CIL. To znamená, že tělo CIL poskytnuté profilerem nemusí být přiděleno pomocí rozhraní [IMethodMalloc](imethodmalloc-interface.md) nebo přiděleno v určitém rozsahu. Může být přiděleno na kterékoli haldě. Profiler může uvolnit paměť, která se používá pro tělo CIL po `SetILFunctionBody` vrácení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerFunctionControl – rozhraní](icorprofilerfunctioncontrol-interface.md)
