---
title: "ICorProfilerInfo::GetILFunctionBody – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 035c2a1926d80b4aaea57523b4ecdd3da6873efe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody – metoda
Získá ukazatel k tělu metody v kódu (MSIL intermediate language) společnosti Microsoft, začínající na jeho záhlaví.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [v] ID modulu, ve kterém se funkce nachází.  
  
 `methodId`  
 [v] Token metadata pro metodu.  
  
 `ppMethodHeader`  
 [out] Ukazatel na záhlaví metody.  
  
 `pcbMethodSize`  
 [out] Celé číslo, které určuje velikost metody.  
  
## <a name="remarks"></a>Poznámky  
 Metoda je vymezen modulu, ve kterém je umístěn. Protože `GetILFunctionBody` metoda je navržená tak, aby poskytl přístup k nástroji kód MSIL předtím, než byl načten modulem common language runtime (CLR), použije token metadata metody najít požadované instance.  
  
 `GetILFunctionBody`CORPROF_E_FUNCTION_NOT_IL HRESULT může vrátit, pokud `methodId` odkazuje na metodu, bez jakékoli MSIL kód (například abstraktní metodu nebo platformu invoke – metoda (PInvoke)).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
