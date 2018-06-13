---
title: FunctionTailcall – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11cf96f5957d41e0647c309a7b0bb08fc9b31c91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452101"
---
# <a name="functiontailcall-function"></a>FunctionTailcall – funkce
Upozorní profileru, že aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce.  
  
> [!NOTE]
>  `FunctionTailcall` Funkce je zastaralé v rozhraní .NET Framework verze 2.0. Bude nadále fungovat, ale bude způsobit snížení výkonu. Použití [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) funkce místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcID`  
 [v] Identifikátor aktuálně prováděné funkce, která se chystáte provést, tail volání.  
  
## <a name="remarks"></a>Poznámky  
 Cíl funkce volání funkce tail použije aktuální rámec zásobníku a vrátí přímo do volající funkce, který vytvořil tail volání. To znamená, že [functionleave –](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) zpětného volání nebude vydán pro funkci, která je cílem volání funkce tail.  
  
 `FunctionTailcall` Je funkce zpětného volání, je nutné implementovat. Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.  
  
 Spouštěcí modul neukládá žádné registry před voláním této funkce.  
  
-   Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).  
  
-   Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.  
  
 Implementace `FunctionTailcall` by neměly blokovat, protože zpozdí uvolňování paměti. Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci. Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionTailcall` vrátí.  
  
 Navíc `FunctionTailcall` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také  
 [FunctionEnter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [SetEnterLeaveFunctionHooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
