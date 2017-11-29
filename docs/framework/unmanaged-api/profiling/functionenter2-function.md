---
title: "FunctionEnter2 – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter2
helpviewer_keywords: FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0aa1d98021dcbfc38721d7f30ad305065dced605
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter2-function"></a>FunctionEnter2 – funkce
Profileru upozorní, že ovládací prvek je předávána funkci a poskytuje informace o zásobníku argumenty rámec a funkce. Tato funkce nahrazuje [functionenter –](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [v] Identifikátor funkce, ke kterému je předán ovládacího prvku.  
  
 `clientData`  
 [v] Identifikátor změnu mapování funkce, které profileru dříve zadán pomocí [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkce.  
  
 `func`  
 [v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku.  
  
 To profileru by měly zpracovávat jako neprůhledného popisovače, který může být předán zpět do modulu provádění v [ICorProfilerInfo2::getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metoda.  
  
 `argumentInfo`  
 [v] Ukazatel [cor_prf_function_argument_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktura, která určuje umístění v paměti funkce argumentů.  
  
 Chcete-li získat přístup k informacím argument `COR_PRF_ENABLE_FUNCTION_ARGS` musí být nastaven příznak. Můžete použít profileru [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodu a nastavit příznaky událostí.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty `func` a `argumentInfo` parametry nejsou platné po `FunctionEnter2` funkce vrátí hodnotu, protože hodnoty může změnit nebo zničena.  
  
 `FunctionEnter2` Je funkce zpětného volání, je nutné implementovat. Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.  
  
 Spouštěcí modul neukládá žádné registry před voláním této funkce.  
  
-   Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).  
  
-   Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.  
  
 Implementace `FunctionEnter2` by neměly blokovat, protože zpozdí uvolňování paměti. Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci. Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionEnter2` vrátí.  
  
 Navíc `FunctionEnter2` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Functionleave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [Functiontailcall2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [Setenterleavefunctionhooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Profilace globálních statických funkcí](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
