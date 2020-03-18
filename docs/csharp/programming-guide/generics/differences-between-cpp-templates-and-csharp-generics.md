---
title: Rozdíly mezi šablonami jazyka C++ a obecnými typy jazyka C# – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: e44f67353410c58c406620109270972df17f9f86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703530"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)
Obecné znaky jazyka C# a šablony jazyka C++ jsou obě funkce jazyka, které poskytují podporu pro parametrizované typy. Nicméně, existuje mnoho rozdílů mezi těmito dvěma. Na úrovni syntaxe c# obecné typy jsou jednodušší přístup k parametrizované typy bez složitosti šablon Jazyka C++. Kromě toho C# nepokouší poskytnout všechny funkce, které poskytují šablony jazyka C++. Na úrovni implementace je primární rozdíl, že nahrazení obecného typu Jazyka C# se provádí za běhu a informace o obecném typu se tak zachovávají pro instance objektů. Další informace naleznete [v tématu Obecné typy v době spuštění](./generics-in-the-run-time.md).  
  
 Níže jsou uvedeny hlavní rozdíly mezi šablonami C# Generics a C++:  
  
- Obecné typy jazyka C# neposkytují stejné množství flexibility jako šablony jazyka C++. Například není možné volat aritmetické operátory v obecné třídě Jazyka C#, i když je možné volat uživatelem definované operátory.  
  
- C# neumožňuje parametry šablony bez typu, například `template C<int i> {}`.  
  
- C# nepodporuje explicitní specializaci; to znamená vlastní implementaci šablony pro určitý typ.  
  
- C# nepodporuje částečnou specializaci: vlastní implementaci pro podmnožinu argumentů typu.  
  
- C# neumožňuje typ parametru, který má být použit jako základní třídy pro obecný typ.  
  
- C# neumožňuje parametry typu mít výchozí typy.  
  
- V c#, obecný typ parametr nemůže být sám obecný, i když konstruované typy lze použít jako obecné. C++ umožňuje parametry šablony.  
  
- C++ umožňuje kód, který nemusí být platný pro všechny parametry typu v šabloně, který je pak zkontrolován pro konkrétní typ použitý jako parametr typu. C# vyžaduje kód ve třídě, které mají být zapsány takovým způsobem, že bude pracovat s libovolným typem, který splňuje omezení. Například v jazyce C++ je možné napsat funkci, která `+` `-` používá aritmetické operátory a na objekty parametru typu, který způsobí chybu v době vytváření instancí šablony s typem, který nepodporuje tyto operátory. C# to zakazuje; pouze jazyk konstrukce povolena jsou ty, které lze odvodit z omezení.  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Šablony](/cpp/cpp/templates-cpp)
