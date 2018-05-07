---
title: ICorProfilerModuleEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 35256a25ed793ffee6ddc1b26088e0988fea5af2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilermoduleenumskip-method"></a>ICorProfilerModuleEnum::Skip – metoda
Posune kurzor enumerátor z aktuálního umístění tak, aby se přeskočí zadaný počet elementů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [v] Počet elementů lze vynechat.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`celt` elementy byly vynechány.|  
|S_FALSE|Méně než `celt` elementy byly přeskočeny, což naznačuje, že neexistují žádné další prvky.|  
  
## <a name="remarks"></a>Poznámky  
 Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerModuleEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
