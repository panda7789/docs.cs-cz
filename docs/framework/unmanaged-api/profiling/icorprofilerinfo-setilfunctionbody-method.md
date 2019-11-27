---
title: ICorProfilerInfo::SetILFunctionBody – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: da81bd3e255898543c94d4ac64c6afbf39b6bdba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449883"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a>ICorProfilerInfo::SetILFunctionBody – metoda
Nahradí tělo zadané funkce v zadaném modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 pro ID modulu, ve kterém je funkce umístěna.  
  
 `methodid`  
 pro Token funkce, pro kterou má být nahrazena tělo  
  
 `pbNewILMethodHeader`  
 pro Nové záhlaví funkce  
  
## <a name="remarks"></a>Poznámky  
 Metoda `SetILFunctionBody` nahradí relativní virtuální adresu funkce v metadatech tak, aby odkazovala na nový text funkce, a podle potřeby upraví všechny interní datové struktury.  
  
 Metodu `SetILFunctionBody` lze volat pouze pro funkce, které nebyly nikdy zkompilovány kompilátorem JIT (just-in-time).  
  
 Pomocí metody [ICorProfilerInfo:: GetILFunctionBodyAllocator –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) přidělte místo pro novou metodu, aby byla zajištěna kompatibilita vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
