---
title: FunctionEnter2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177056"
---
# <a name="functionenter2-function"></a>FunctionEnter2 – funkce
Upozorní profiler, že ovládací prvek je předáván funkci a poskytuje informace o argumentech rámce zásobníku a funkce. Tato funkce nahrazuje funkci [FunctionEnter.](functionenter-function.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[in] Identifikátor funkce, které je ovládací prvek předán.

- `clientData`

  \[in] Přemapovaný identifikátor funkce, který profiler dříve zadal pomocí funkce [FunctionIDMapper.](functionidmapper-function.md)
  
- `func`

  \[in] `COR_PRF_FRAME_INFO` Hodnota, která odkazuje na informace o rámci zásobníku.
  
  Profiler by měl považovat za neprůhledný popisovač, který může být předán zpět do modulu provádění v [Metodě ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- `argumentInfo`

  \[in] Ukazatel na [strukturu COR_PRF_FUNCTION_ARGUMENT_INFO,](cor-prf-function-argument-info-structure.md) která určuje umístění v paměti argumentů funkce.

  Chcete-li získat přístup `COR_PRF_ENABLE_FUNCTION_ARGS` k informacím o argumentech, musí být příznak nastaven. Profiler můžete použít [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) metoda nastavit příznaky události.

## <a name="remarks"></a>Poznámky  
 Hodnoty `func` a `argumentInfo` parametry nejsou platné po `FunctionEnter2` vrátí funkce, protože hodnoty mohou změnit nebo být zničeny.  
  
 Funkce `FunctionEnter2` je zpětné volání; musíte jej implementovat. Implementace musí používat `__declspec``naked`atribut ( ) třídy úložiště.  
  
 Spuštění motoru neukládá žádné registry před voláním této funkce.  
  
- Při vstupu je nutné uložit všechny registry, které používáte, včetně registrů v jednotce s plovoucí desetinnou tálicí (FPU).  
  
- Při ukončení je nutné obnovit zásobník odprýskávání mačkání všechny parametry, které byly posunuty jeho volajícího.  
  
 Implementace `FunctionEnter2` by nemělblokovat, protože zpozdí uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu vhodném pro uvolnění paměti. Pokud dojde k pokusu o uvolnění paměti, zaběhu se zablokuje, dokud `FunctionEnter2` se vrátí.  
  
 `FunctionEnter2` Funkce také nesmí volat do spravovaného kódu nebo žádným způsobem způsobit přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [FunctionLeave2 – funkce](functionleave2-function.md)
- [FunctionTailcall2 – funkce](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 – metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
