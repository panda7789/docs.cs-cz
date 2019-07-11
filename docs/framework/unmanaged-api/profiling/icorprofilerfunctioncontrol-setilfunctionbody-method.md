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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d831dd7a63c06327bb0f373b3be254401c6e2ee9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780358"
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
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Nahrazení proběhlo úspěšně.|  
  
## <a name="remarks"></a>Poznámky  
 Na rozdíl od [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody, `SetILFunctionBody` spravuje paměť potřebnou pro nové tělo CIL. To znamená, že tělo CIL poskytnuté profilerem nemusí být přiděleno pomocí [imethodmalloc –](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) rozhraní nebo v určitém rozsahu. Může být přiděleno na kterékoli haldě. Profiler může uvolnit paměť používanou pro jeho tělo CIL po `SetILFunctionBody` vrátí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerFunctionControl – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
