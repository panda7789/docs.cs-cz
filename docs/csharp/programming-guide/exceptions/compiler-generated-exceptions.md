---
title: Výjimky generované kompilátorem – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 2a6b2c3fa053f1c555856df8098975340e78e2b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705311"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Výjimky generované kompilátorem (Průvodce programováním v C#)
Některé výjimky jsou vyvolány automaticky v rámci .NET Framework je společný jazyk runtime (CLR) při selhání základní operace. Tyto výjimky a jejich chybové stavy jsou uvedeny v následující tabulce.  
  
|Výjimka|Popis|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Základní třída pro výjimky, ke kterým dochází během <xref:System.DivideByZeroException> <xref:System.OverflowException>aritmetických operací, například a .|  
|<xref:System.ArrayTypeMismatchException>|Vyvolána, když pole nelze uložit daný prvek, protože skutečný typ prvku je nekompatibilní s aktuální typ pole.|  
|<xref:System.DivideByZeroException>|Vyvolána při pokusu o rozdělení integrální hodnoty nulou.|  
|<xref:System.IndexOutOfRangeException>|Vyvolána při pokusu o index pole, pokud je index menší než nula nebo mimo hranice pole.|  
|<xref:System.InvalidCastException>|Vyvolána při explicitní převod ze základního typu do rozhraní nebo odvozeného typu selže za běhu.|  
|<xref:System.NullReferenceException>|Vyvolána při pokusu o odkaz na objekt, jehož hodnota je [null](../../language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Vyvolána při pokusu o přidělení paměti pomocí [nového](../../language-reference/operators/new-operator.md) operátoru se nezdaří. To znamená, že paměť dostupná pro běžný jazyk runtime byla vyčerpána.|  
|<xref:System.OverflowException>|Vyvolána při aritmetické operace `checked` v kontextu přetečení.|  
|<xref:System.StackOverflowException>|Vyvolána při spuštění zásobníku je vyčerpán tím, že příliš mnoho čekající volání metody; obvykle označuje velmi hlubokou nebo nekonečnou rekurzi.|  
|<xref:System.TypeInitializationException>|Vyvolána, když statický konstruktor vyvolá výjimku a neexistuje žádná kompatibilní `catch` klauzule, která by ji zachytila.|  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Výjimky a zpracování výjimek](./index.md)
- [Zpracování výjimek](./exception-handling.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
