---
title: "Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aea1b51c26a8f3de56ea66b9cf89e75bfeb59d81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)
Šablony obecnými typy C# a C++ jsou obě jazykové funkce, které poskytují podporu pro parametrizované typy. Existují však mnoho rozdíly mezi nimi. Na úrovni syntaxe obecnými typy C# jsou jednodušší přístup k parametrizované typy bez složitost C++ šablon. Kromě toho C# nepokouší poskytnout všechny funkce, které poskytují šablonami C++. Na úrovni implementace základní rozdíl je, že náhrady obecného typu C# jsou prováděny v době běhu a instancí objektů se tím zachovají informace obecného typu. Další informace najdete v tématu [obecné typy v čase spuštění](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 Tady jsou klíčové rozdíly mezi šablony C++ a obecnými typy C#:  
  
-   Obecnými typy C# neposkytují stejnou úroveň flexibilitu jako šablony jazyka C++. Není například možné volat aritmetické operátory v jazyce C# obecné třídy, přestože je možné volat uživatelem definovaných operátorů.  
  
-   C# neumožňuje parametry šablon bez typu, například `template C<int i> {}`.  
  
-   C# nepodporuje explicitní specializace; To znamená, vlastní implementaci šablonu pro konkrétní typ.  
  
-   C# nepodporuje částečná specializace: vlastní implementace pro podmnožinu argumenty typu.  
  
-   C# neumožňuje parametr typu, který se má použít jako základní třída pro obecný typ.  
  
-   C# neumožňuje parametry typu do mají výchozí typy.  
  
-   V jazyce C# parametr obecného typu samotné nelze obecný, i když sestavené typy lze použít jako obecné typy. C++ povolit parametry šablony.  
  
-   C++ umožňuje kód, který nemusí platit pro všechny parametry typu v šabloně, která kontroluje pro konkrétní typ použít jako parametr typu. C# vyžaduje kód ve třídě k zapsání tak, že bude fungovat s žádný typ, který splňuje omezení. Například v jazyce C++ je možné vytvořit funkci, která používá aritmetické operátory `+` a `-` u objektů typu parametru, která způsobí chybu v době vytvoření instance šablony s typem, který nepodporuje tyto operátory. C# zakáže to; pouze jazykové konstrukty povolené jsou ty, které lze odvodit z omezení.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Šablony](/cpp/cpp/templates-cpp)
