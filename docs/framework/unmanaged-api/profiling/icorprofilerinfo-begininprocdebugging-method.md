---
title: "ICorProfilerInfo::BeginInprocDebugging – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.BeginInprocDebugging
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91306bbea7b099f7e9e408f8bf69625f1d7da68e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging – metoda
Inicializuje ladění podpory v procesu. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fThisThreadOnly`  
 [v] Nastavte tuto hodnotu na `true` inicializovat ladění podporu pro pouze aktuální vlákno; nastavte ji na `false` inicializovat ladění podporu pro všechna vlákna.  
  
 `pdwProfilerContext`  
 [out] Ukazatel na vrácené hodnoty, který identifikuje relaci ladění.  
  
## <a name="remarks"></a>Poznámky  
 Ladění služby CLR podporované omezené v procesu ladění v rozhraní .NET Framework verze 1.0 a 1.1. V procesu ladění povoleno profileru používat části kontroly rozhraní API pro ladění. Však z důvodu zpětné vazby zákazníka, v rámci procesu ladění má byla odebrána z rozhraní .NET Framework verze 2.0 a nahradí sadu funkcí, které je větší souladu profilaci API.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.0  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
