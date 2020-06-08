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
ms.openlocfilehash: 5984c63f0e1a1859dd5cc2550d6dc37c963affb3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503000"
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
 Metoda je vymezena modulem, ve kterém žije. Vzhledem k tomu, že `GetILFunctionBody` Metoda je navržena tak, aby před tím, než je načtena modulem CLR (Common Language Runtime), dala nástroji přístup k kódu jazyka MSIL, používá k nalezení požadované instance token metadat metody.  
  
 `GetILFunctionBody`může vrátit CORPROF_E_FUNCTION_NOT_IL HRESULT `methodId` , pokud odkazuje na metodu bez jakéhokoli kódu jazyka MSIL (jako je abstraktní metoda nebo metoda Invoke platformy (PInvoke)).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
