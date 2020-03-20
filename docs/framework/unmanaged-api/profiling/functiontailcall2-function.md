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
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175184"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 – funkce
Upozorní profiler, že aktuálně spuštěná funkce se chystá provést volání ocasu na jinou funkci a poskytuje informace o rámci zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[in] Identifikátor aktuálně vykonávající funkce, která se chystá provést volání ocasu.

- `clientData`

  \[in] Přemapovaný identifikátor funkce, který profiler dříve zadal prostřednictvím [FunctionIDMapper](functionidmapper-function.md), aktuálně spuštěné funkce, která se chystá provést volání ocasu.
  
- `func`

  \[in] `COR_PRF_FRAME_INFO` Hodnota, která odkazuje na informace o rámci zásobníku.

  Profiler by měl považovat za neprůhledný popisovač, který může být předán zpět do modulu provádění v [Metodě ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)

## <a name="remarks"></a>Poznámky  
 Cílová funkce volání ocasu použije aktuální rámec zásobníku a vrátí se přímo volajícímu funkce, která provedla volání ocasu. To znamená, že zpětné volání [FunctionLeave2](functionleave2-function.md) nebude vydána pro funkci, která je cílem volání ocasu.  
  
 Hodnota parametru `func` není platná po `FunctionTailcall2` vrátí funkce, protože hodnota může změnit nebo být zničena.  
  
 Funkce `FunctionTailcall2` je zpětné volání; musíte jej implementovat. Implementace musí používat `__declspec``naked`atribut ( ) třídy úložiště.  
  
 Spuštění motoru neukládá žádné registry před voláním této funkce.  
  
- Při vstupu je nutné uložit všechny registry, které používáte, včetně registrů v jednotce s plovoucí desetinnou tálicí (FPU).  
  
- Při ukončení je nutné obnovit zásobník odprýskávání mačkání všechny parametry, které byly posunuty jeho volajícího.  
  
 Implementace `FunctionTailcall2` by nemělblokovat, protože zpozdí uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu vhodném pro uvolnění paměti. Pokud dojde k pokusu o uvolnění paměti, zaběhu se zablokuje, dokud `FunctionTailcall2` se vrátí.  
  
 `FunctionTailcall2` Funkce také nesmí volat do spravovaného kódu nebo žádným způsobem způsobit přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [FunctionEnter2 – funkce](functionenter2-function.md)
- [FunctionLeave2 – funkce](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 – metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
