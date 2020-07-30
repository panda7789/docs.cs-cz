---
title: Rozdíly mezi šablonami C++ a obecnými typy C# – Průvodce programováním v C#
description: Přečtěte si o rozdílech mezi šablonami C++ a obecnými typy C#. Oba jsou jazykové funkce, které poskytují podporu pro parametrizované typy.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: f405e2d4bef730317703b3b8470edef5b89f0bed
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301928"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)
Obecné typy a šablony jazyka C++ jsou funkce jazyka, které poskytují podporu pro parametrizované typy. Existuje však mnoho rozdílů mezi těmito dvěma. Na úrovni syntaxe jsou obecné typy C# jednodušší přístup k parametrizovaným typům bez složitosti šablon jazyka C++. Kromě toho C# nepokusí o poskytnutí všech funkcí, které poskytují šablony jazyka C++. Na úrovni implementace je hlavním rozdílem, že nahrazení obecného typu jazyka C# jsou prováděna za běhu a informace o obecném typu jsou zachovány pro instance objektů. Další informace naleznete v tématu [Obecné typy v době běhu](./generics-in-the-run-time.md).  
  
 Níže jsou uvedené klíčové rozdíly mezi obecnými typy C# a šablonami jazyka C++:  
  
- Obecné typy jazyka C# neposkytují stejné množství flexibility jako šablony jazyka C++. Například není možné volat aritmetické operátory v obecné třídě C#, i když je možné volat operátory definované uživatelem.  
  
- Jazyk C# nepovoluje parametry šablony bez typu, například `template C<int i> {}` .  
  
- Jazyk C# nepodporuje explicitní specializaci; To znamená vlastní implementace šablony pro konkrétní typ.  
  
- Jazyk C# nepodporuje částečnou specializaci: vlastní implementaci pro podmnožinu argumentů typu.  
  
- Jazyk C# nepovoluje, aby byl parametr typu použit jako základní třída pro obecný typ.  
  
- Jazyk C# nepovoluje, aby parametry typu měly výchozí typy.  
  
- V jazyce C# nemůže být parametr obecného typu sám obecný, i když konstruované typy lze použít jako obecné. Jazyk C++ povoluje parametry šablony.  
  
- Jazyk C++ umožňuje kód, který nemusí být platný pro všechny parametry typu v šabloně, která je poté kontrolována pro konkrétní typ použitý jako parametr typu. Jazyk C# vyžaduje, aby kód ve třídě byl napsán takovým způsobem, který bude fungovat s jakýmkoli typem, který splňuje omezení. Například v jazyce C++ je možné napsat funkci, která používá aritmetické operátory `+` a `-` objekty parametru typu, což způsobí chybu v době vytváření instance šablony s typem, který tyto operátory nepodporuje. C# to nepovoluje; jsou povoleny pouze jazykové konstrukce, které lze odvodit z omezení.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Šablony](/cpp/cpp/templates-cpp)
