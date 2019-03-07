---
title: ICorProfilerModuleEnum::Clone – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd3e3739ea9b5330f456156c0455009d90478649
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470468"
---
# <a name="icorprofilermoduleenumclone-method"></a>ICorProfilerModuleEnum::Clone – metoda
Získá ukazatel rozhraní na kopii této [icorprofilermoduleenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Ukazatel na ukazatel rozhraní, které zase odkazuje na kopii této [icorprofilermoduleenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) rozhraní. Kopírování čítač udržuje svůj vlastní stav výčtu odděleně od výčet. Pozice kurzoru počáteční kopie je však stejný jako tento enumerátor aktuálním umístěním kurzoru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerModuleEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
