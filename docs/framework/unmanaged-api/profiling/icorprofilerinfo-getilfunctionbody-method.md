---
title: ICorProfilerInfo::GetILFunctionBody – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
ms.openlocfilehash: a7ec50c91ce02958d0d44643d4f79da1680532aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450356"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody – metoda
Získá ukazatel na tělo metody v kódu jazyka MSIL (Microsoft Intermediate Language) od jejího záhlaví.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 pro ID modulu, ve kterém je funkce umístěna.  
  
 `methodId`  
 pro Token metadat pro metodu  
  
 `ppMethodHeader`  
 mimo Ukazatel na záhlaví metody.  
  
 `pcbMethodSize`  
 mimo Celé číslo, které určuje velikost metody.  
  
## <a name="remarks"></a>Poznámky  
 Metoda je vymezena modulem, ve kterém žije. Vzhledem k tomu, že metoda `GetILFunctionBody` je navržena tak, aby před tím, než je načtena modulem CLR (Common Language Runtime), dala nástroji přístup k kódu jazyka MSIL, používá k nalezení požadované instance token metadat metody.  
  
 `GetILFunctionBody` může vracet CORPROF_E_FUNCTION_NOT_IL HRESULT, pokud `methodId` odkazuje na metodu bez jakéhokoli kódu jazyka MSIL (jako je abstraktní metoda nebo metoda Invoke platformy (PInvoke)).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
