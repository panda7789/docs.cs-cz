---
title: ICorProfilerInfo::GetFunctionFromIP – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fba01c1dfdea83b2580f45b7dbcef91fb7b73fb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452901"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a>ICorProfilerInfo::GetFunctionFromIP – metoda
Mapuje ukazatel instrukce spravovaného kódu `FunctionID`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ip`  
 [v] Ukazatel instrukce ve spravovaném kódu.  
  
 `pFunctionId`  
 [out] ID vrácený funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
