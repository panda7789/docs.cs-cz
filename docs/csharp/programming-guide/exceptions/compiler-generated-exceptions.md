---
title: Výjimky generované kompilátorem – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 4be85bee5fe9c0eeba1c83ac7f79e922c127cc9c
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559562"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Výjimky generované kompilátorem (Průvodce programováním v C#)
Některé výjimky jsou vyvolány automaticky modulem CLR .NET Framework modul CLR (Common Language Runtime), pokud selže základní operace. Tyto výjimky a jejich chybové podmínky jsou uvedeny v následující tabulce.  
  
|Výjimka|Popis|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Základní třída pro výjimky, ke kterým dochází během aritmetických operací, například <xref:System.DivideByZeroException> a <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Vyvolána, když pole nemůže uložit daný element, protože skutečný typ elementu je nekompatibilní se skutečným typem pole.|  
|<xref:System.DivideByZeroException>|Vyvolána při pokusu o rozdělení celočíselné hodnoty nulou.|  
|<xref:System.IndexOutOfRangeException>|Vyvolána při pokusu o indexování pole, když je index menší než nula nebo mimo hranice pole.|  
|<xref:System.InvalidCastException>|Vyvolá se v případě, že při spuštění dojde k chybě explicitního převodu ze základního typu na rozhraní nebo na odvozený typ.|  
|<xref:System.NullReferenceException>|Vyvolána, když se provede pokus o odkaz na objekt, jehož hodnota je [null](../../language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Vyvolá se v případě, že pokus o přidělení paměti pomocí operátoru [New](../../language-reference/operators/new-operator.md) se nezdařil. To znamená, že byla vyčerpána paměť dostupná pro modul CLR (Common Language Runtime).|  
|<xref:System.OverflowException>|Vyvoláno, když dojde k přetečení aritmetické operace v kontextu `checked`.|  
|<xref:System.StackOverflowException>|Vyvoláno při vyčerpání zásobníku spouštění pomocí příliš velkého počtu volání metod, které čekají na zpracování; obvykle označuje velmi hlubokou nebo nekonečnou rekurzi.|  
|<xref:System.TypeInitializationException>|Vyvolána, když statický konstruktor vyvolá výjimku a neexistuje žádná kompatibilní klauzule `catch` pro zachycení.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Výjimky a jejich zpracování](./index.md)
- [Zpracování výjimek](./exception-handling.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
