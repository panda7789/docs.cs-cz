---
title: "Výjimky generované kompilátorem (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d1417e42f588978d5fc1beca4ad55463502ee219
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Výjimky generované kompilátorem (Průvodce programováním v C#)
Některé výjimky jsou vyvolány automaticky pomocí rozhraní .NET Framework common language runtime (CLR), pokud základní operace s chybou. Tyto výjimky a jejich chybové stavy jsou uvedeny v následující tabulce.  
  
|Výjimka|Popis|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Základní třída pro výjimky, které se vyskytnou při aritmetické operace, jako například <xref:System.DivideByZeroException> a <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Vyvolá, když pole nelze uložit daného elementu, protože skutečný typ elementu není kompatibilní s skutečný typ pole.|  
|<xref:System.DivideByZeroException>|Vyvolá, když je učiněn pokus o hodnotu celočíselné dělení nulou.|  
|<xref:System.IndexOutOfRangeException>|Vyvolá, když je proveden pokus o indexu pole při index je menší než nula nebo mimo rozsah pole.|  
|<xref:System.InvalidCastException>|Vyvolá, když explicitní převod z typu základní rozhraní nebo odvozený typ selže za běhu.|  
|<xref:System.NullReferenceException>|Při pokusu o odkazují na objekt, jehož hodnota je [null](../../../csharp/language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Při pokusu o přidělení paměti pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md) operátor selže. To znamená, že byl vyčerpán paměti k dispozici pro modul common language runtime.|  
|<xref:System.OverflowException>|Vyvolá, když aritmetické operace v `checked` přeteče mimo kontext.|  
|<xref:System.StackOverflowException>|Při provádění zásobníku vyčerpá tak, že jsou příliš mnoha volání čekající metoda; obvykle to znamená velmi hloubkové nebo nekonečné rekurzi.|  
|<xref:System.TypeInitializationException>|Vyvolá, když statického konstruktoru výjimku a kompatibilní `catch` existuje klauzule k zachycení ho.|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)  
 [Zpracování výjimek](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [try-catch –](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally –](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally –](../../../csharp/language-reference/keywords/try-catch-finally.md)
