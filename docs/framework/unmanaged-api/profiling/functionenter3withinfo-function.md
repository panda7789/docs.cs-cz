---
title: "FunctionEnter3WithInfo – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3WithInfo
api_location: mscorwks.cll
api_type: COM
f1_keywords: FunctionEnter3WithInfo
helpviewer_keywords: FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 37cdf823cc910dd1cebcb587d2616406a842fef2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter3withinfo-function"></a>FunctionEnter3WithInfo – funkce
Profileru upozorní, že se ovládací prvek předán do funkce a poskytuje popisovač, který se dá předat do [icorprofilerinfo3::getfunctionenter3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) k načtení argumentů rámec a funkce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionIDOrClientID`  
 [v] Identifikátor funkce, ke kterému je předán ovládacího prvku.  
  
 `eltInfo`  
 [v] Neprůhledného popisovače, který představuje informace o daném zásobníku. Tento popisovač je platný pouze během zpětného volání, ke kterému je předán.  
  
## <a name="remarks"></a>Poznámky  
 `FunctionEnter3WithInfo` Metoda zpětného volání upozorní profileru jako funkce se nazývají a umožňuje profileru používat [icorprofilerinfo3::getfunctionenter3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) ke kontrole hodnot argumentů. Pro přístup k informacím argument `COR_PRF_ENABLE_FUNCTION_ARGS` příznak musí být nastavena. Můžete použít profileru [icorprofilerinfo::seteventmask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) nastavte příznaky událostí, a pak použít [icorprofilerinfo3::setenterleavefunctionhooks3withinfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci vaší implementace této funkce.  
  
 `FunctionEnter3WithInfo` Je funkce zpětného volání, je nutné implementovat. Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.  
  
 Spouštěcí modul neukládá žádné registry před voláním této funkce.  
  
-   Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).  
  
-   Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.  
  
 Implementace `FunctionEnter3WithInfo` by neměly blokovat, protože zpozdí uvolňování paměti. Implementace neměli uvolňování, protože zásobník nemusí být ve stavu paměti procházející kolekci. Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionEnter3WithInfo` vrátí.  
  
 `FunctionEnter3WithInfo` Funkce nesmí volání do spravovaného kódu nebo způsobit přidělení spravované paměti žádným způsobem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Getfunctionenter3info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)  
 [Functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [Functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [Profilace globálních statických funkcí](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
