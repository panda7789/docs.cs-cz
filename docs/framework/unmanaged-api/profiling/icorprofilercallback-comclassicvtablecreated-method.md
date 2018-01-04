---
title: "ICorProfilerCallback::COMClassicVTableCreated – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.COMClassicVTableCreated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43fb447393e1d34ca53fbb62ecdc456a97452bc4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a>ICorProfilerCallback::COMClassicVTableCreated – metoda
Vytvořený COM spolupráce tabulce vtable pro zadaný identifikátor IID a třída upozorní profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wrappedClasId`  
 [v] ID třídy, pro kterou byly vytvořeny tabulce vtable.  
  
 `implementedIID`  
 [v] ID rozhraní implementované třídou. Tato hodnota může mít hodnotu NULL, pokud rozhraní je jenom interní.  
  
 `pVTable`  
 [v] Ukazatel na spuštění tabulce vtable.  
  
 `cSlots`  
 [v] Počet sloty, které jsou v tabulce vtable.  
  
## <a name="remarks"></a>Poznámky  
 Profileru by neměly blokovat v jeho implementace této metody, protože zásobník nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti. Pokud zde blokuje profileru a dojde k pokusu o uvolňování paměti, modul runtime se zablokuje, dokud se vrátí tato zpětného volání.  
  
 Okna profilování implementace této metody by neměla volání do spravovaného kódu nebo v žádné příčina způsob přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [COMClassicVTableDestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
