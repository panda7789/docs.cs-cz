---
title: ICorProfilerInfo::GetInprocInspectionInterface – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 761dd55d2ae48739f24a03b8ce81c571fb211a5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a>ICorProfilerInfo::GetInprocInspectionInterface – metoda
Získá objekt, který může být dotazován pro rozhraní "ICorDebugProcess". Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppicd`  
 [out](/cpp/atl/iunknown) objekt, který může být dotazován pro `ICorDebugProcess` rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (CLR) rozhraní API pro ladění podporována omezené v procesu ladění v rozhraní .NET Framework verze 1.0. V procesu ladění povoleno profileru používat části kontroly rozhraní API pro ladění. V důsledku názory zákazníků v procesu ladění bylo odstraněno z rozhraní .NET Framework verze 2.0 a nahradí sadu funkcí, které je větší souladu profilaci API.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.0  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
