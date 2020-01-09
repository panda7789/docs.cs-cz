---
title: Rozdíly mezi C++ šablonami C# a obecnými C# typy – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: e44f67353410c58c406620109270972df17f9f86
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703530"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)
C#Obecné typy a C++ šablony jsou obě funkce jazyka, které poskytují podporu pro parametrizované typy. Existuje však mnoho rozdílů mezi těmito dvěma. Na úrovni syntaxe C# obecné jsou jednodušší přístup k parametrizovaným typům bez složitosti C++ šablon. Kromě toho C# se nepokouší poskytovat všechny funkce, které C++ poskytují šablony. Na úrovni implementace je hlavním rozdílem, že C# nahrazení obecného typu jsou prováděna za běhu a informace o obecném typu jsou zachovány pro instance objektů. Další informace naleznete v tématu [Obecné typy v době běhu](./generics-in-the-run-time.md).  
  
 Níže jsou uvedené klíčové rozdíly mezi C# obecnými a C++ šablonami:  
  
- C#Obecné typy neposkytují stejné množství flexibility jako C++ šablony. Například není možné volat aritmetické operátory v C# obecné třídě, i když je možné volat operátory definované uživatelem.  
  
- C#nepovoluje parametry šablony bez typu, například `template C<int i> {}`.  
  
- C#nepodporuje explicitní specializaci; To znamená vlastní implementace šablony pro konkrétní typ.  
  
- C#nepodporuje částečnou specializaci: vlastní implementaci pro podmnožinu argumentů typu.  
  
- C#nepovoluje, aby byl parametr typu použit jako základní třída pro obecný typ.  
  
- C#nepovoluje, aby parametry typu měly výchozí typy.  
  
- V C#, obecný parametr typu nemůže být obecný, i když konstruované typy lze použít jako obecné. C++povolí parametry šablony.  
  
- C++povoluje kód, který nemusí být platný pro všechny parametry typu v šabloně, která je poté kontrolována pro konkrétní typ použitý jako parametr typu. C#vyžaduje, aby kód ve třídě byl napsán takovým způsobem, který bude fungovat s jakýmkoli typem, který splňuje omezení. Například C++ je možné napsat funkci, která používá aritmetické operátory `+` a `-` v objektech parametru typu, který vytvoří chybu v době vytváření instance šablony s typem, který tyto operátory nepodporuje. C#nepovoluje se. jsou povoleny pouze jazykové konstrukce, které lze odvodit z omezení.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Šablony](/cpp/cpp/templates-cpp)
