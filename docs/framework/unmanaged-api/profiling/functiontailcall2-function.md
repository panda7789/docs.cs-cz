---
title: FunctionTailcall2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a515c2622f81c666523aa012fa1e34e5251c074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 – funkce
Profileru upozorní, že aktuálně prováděné funkce provede volání funkce tail do jiné funkce a poskytuje informace o rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [v] Identifikátor aktuálně prováděné funkce, která se chystáte provést, tail volání.  
  
 `clientData`  
 [v] Identifikátor změnu mapování funkce, které profileru dříve zadán prostřednictvím [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), aktuálně prováděné funkce, která se chystáte provést, tail volání.  
  
 `func`  
 [v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku.  
  
 To profileru by měly zpracovávat jako neprůhledného popisovače, který může být předán zpět do modulu provádění v [ICorProfilerInfo2::getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metoda.  
  
## <a name="remarks"></a>Poznámky  
 Cíl funkce volání funkce tail použije aktuální rámec zásobníku a vrátí přímo do volající funkce, který vytvořil tail volání. To znamená, že [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zpětného volání nebude vydán pro funkci, která je cílem volání funkce tail.  
  
 Hodnota `func` parametr není platný po `FunctionTailcall2` funkce vrátí hodnotu, protože hodnota může změnit nebo zničena.  
  
 `FunctionTailcall2` Je funkce zpětného volání, je nutné implementovat. Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.  
  
 Spouštěcí modul neukládá žádné registry před voláním této funkce.  
  
-   Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).  
  
-   Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.  
  
 Implementace `FunctionTailcall2` by neměly blokovat, protože zpozdí uvolňování paměti. Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci. Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionTailcall2` vrátí.  
  
 Navíc `FunctionTailcall2` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [FunctionEnter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [SetEnterLeaveFunctionHooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
