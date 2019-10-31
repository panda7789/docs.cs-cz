---
title: Globální statické funkce ladění
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: 965724c1e937fa62f05c33b0dcf8a5c8b9e1b029
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124320"
---
# <a name="debugging-global-static-functions"></a>Globální statické funkce ladění
Tato část popisuje nespravované globální statické funkce, které používá rozhraní API pro ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [_EFN_GetManagedExcepStack – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 Pokud je zadána adresa spravovaného objektu výjimky, vrátí verzi řetězce trasování zásobníku obsaženého v rámci.  
  
 [_EFN_GetManagedObjectFieldInfo – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 Získá posun od začátku objektu k poli a hodnotu pole pomocí zadaného ukazatele objektu a názvu pole.  
  
 [_EFN_GetManagedObjectName – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 Získá název typu pomocí zadaného ukazatele spravovaného objektu.  
  
 [_EFN_StackTrace – funkce](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 Poskytuje textovou reprezentaci spravovaného trasování zásobníku a pole `CONTEXT` záznamů, jednu pro každý přechod mezi nespravovaným a spravovaným kódem.  
  
 [CLRDataCreateInstance – funkce](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 Volá se službami CLR (Common Language Runtime) k vytvoření zadaného objektu rozhraní pro zadaný cílový proces.  
  
 [PFN_CLRDataCreateInstance – ukazatel na funkci](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 Odkazuje na funkci, která je volána službami CLR Data Access, k vytvoření zadaného objektu rozhraní pro zadaný cílový proces.  
  
## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
