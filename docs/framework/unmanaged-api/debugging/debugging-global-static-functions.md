---
title: Globální statické funkce ladění
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: c20d8719b63cb40074dc740506ae4a3c0fc3a251
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793784"
---
# <a name="debugging-global-static-functions"></a>Globální statické funkce ladění
Tato část popisuje nespravované globální statické funkce, které používá rozhraní API pro ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [_EFN_GetManagedExcepStack – funkce](efn-getmanagedexcepstack-function.md)  
 Pokud je zadána adresa spravovaného objektu výjimky, vrátí verzi řetězce trasování zásobníku obsaženého v rámci.  
  
 [_EFN_GetManagedObjectFieldInfo – funkce](efn-getmanagedobjectfieldinfo-function.md)  
 Získá posun od začátku objektu k poli a hodnotu pole pomocí zadaného ukazatele objektu a názvu pole.  
  
 [_EFN_GetManagedObjectName – funkce](efn-getmanagedobjectname-function.md)  
 Získá název typu pomocí zadaného ukazatele spravovaného objektu.  
  
 [_EFN_StackTrace – funkce](efn-stacktrace-function.md)  
 Poskytuje textovou reprezentaci spravovaného trasování zásobníku a pole `CONTEXT` záznamů, jednu pro každý přechod mezi nespravovaným a spravovaným kódem.  
  
 [CLRDataCreateInstance – funkce](clrdatacreateinstance-function.md)  
 Volá se službami CLR (Common Language Runtime) k vytvoření zadaného objektu rozhraní pro zadaný cílový proces.  
  
 [PFN_CLRDataCreateInstance – ukazatel na funkci](pfn-clrdatacreateinstance-function-pointer.md)  
 Odkazuje na funkci, která je volána službami CLR Data Access, k vytvoření zadaného objektu rozhraní pro zadaný cílový proces.  
  
## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro ladění](debugging-coclasses.md)  
  
 [Rozhraní pro ladění](debugging-interfaces.md)  
  
 [Výčty pro ladění](debugging-enumerations.md)  
  
 [Struktury pro ladění](debugging-structures.md)
