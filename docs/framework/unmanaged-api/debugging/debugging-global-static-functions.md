---
title: Globální statické funkce ladění
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2403d736d031aab52525fc12b5071e764a8bde1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-global-static-functions"></a>Globální statické funkce ladění
Tato část popisuje nespravované globální statické funkce, které používá rozhraní API pro ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [_EFN_GetManagedExcepStack – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 Zadaný objekt adresu spravovaného výjimka vrátí řetězec verzi nachází v trasování zásobníku.  
  
 [_EFN_GetManagedObjectFieldInfo – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 Získá posun od začátku objekt pole a hodnotu pole pomocí ukazatele zadaného objektu a název pole.  
  
 [_EFN_GetManagedObjectName – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 Získá název typu pomocí ukazatele zadaný spravovaného objektu.  
  
 [_EFN_StackTrace – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 Poskytuje textové reprezentace trasování spravované zásobníku a pole `CONTEXT` zaznamenává, jednu pro každý přechod mezi nespravované a spravované kódu.  
  
 [CLRDataCreateInstance – funkce](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup k vytvoření objektu zadaného rozhraní pro zadaný cílový proces.  
  
 [PFN_CLRDataCreateInstance – ukazatel na funkci](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 Odkazuje na funkci, která je volána daty CLR přístup ke službám k vytvoření objektu zadaného rozhraní pro zadaný cílový proces.  
  
## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
