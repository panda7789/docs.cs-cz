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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698522"
---
# <a name="debugging-global-static-functions"></a>Globální statické funkce ladění
Tato část popisuje nespravované globální statické funkce, které používá rozhraní API pro ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [_EFN_GetManagedExcepStack – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 Zadaný objekt na spravované výjimky adresu vrátí řetězec verzi obsažena v trasování zásobníku.  
  
 [_EFN_GetManagedObjectFieldInfo – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 Získá posun od začátku objekt pole a hodnota pole pomocí ukazatele zadaného objektu a název pole.  
  
 [_EFN_GetManagedObjectName – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 Získá název typu pomocí ukazatele zadaný spravovaný objekt.  
  
 [_EFN_StackTrace – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 Poskytuje textové vyjádření spravovaného zásobníku a pole `CONTEXT` záznamy, jeden pro každý přechod mezi nespravované a spravovaného kódu.  
  
 [CLRDataCreateInstance – funkce](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 Je voláno common language runtime (CLR) data access services k vytvoření objektu zadané rozhraní pro zadaný cílový proces.  
  
 [PFN_CLRDataCreateInstance – ukazatel na funkci](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 Odkazuje na funkci, která je volána z dat CLR přístup ke službám vytvořit objekt zadané rozhraní pro zadaný cílový proces.  
  
## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
