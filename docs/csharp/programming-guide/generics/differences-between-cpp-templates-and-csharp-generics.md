---
title: Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: eef2fc5919f405b75be7ae2a2069b1e7cf8a45a7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44088073"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)
Šablony obecnými typy C# a C++ jsou obě vlastnosti jazyka, které poskytují podporu pro parametrizované typy. Existují však mnoho rozdíly mezi nimi. Na úrovni syntaxe obecnými typy C# jsou jednodušší přístup k parametrizované typy bez složitosti šablon jazyka C++. Kromě toho C# nepokouší poskytují všechny funkce, které poskytují šablony jazyka C++. Na úrovni implementace základní rozdíl je, že nahrazení obecného typu C# jsou prováděny v době běhu a instance objektů se tak zachovají informace obecného typu. Další informace najdete v tématu [obecné typy v čase spuštění](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 Toto jsou hlavní rozdíly mezi obecnými typy C# a šablony C++:  
  
-   Obecnými typy C# neposkytuje velkou flexibilitu jako šablony jazyka C++. Například není možné volat aritmetických operátorů v jazyce C# generické třídě, i když je možné volat uživatelem definovaných operátorů.  
  
-   C# nepovoluje parametry šablony bez typu, jako například `template C<int i> {}`.  
  
-   C# nepodporuje explicitní specializace; To znamená, vlastní implementaci šablonu pro konkrétního typu.  
  
-   C# nepodporuje částečná specializace: vlastní implementaci pro podmnožinu argumentů typu.  
  
-   C# nepovoluje parametr typu má být použit jako základní třída pro obecného typu.  
  
-   C# nepovoluje typové parametry mají výchozí typy.  
  
-   V jazyce C# parametr obecného typu nemůže být sám obecný, i když sestavené typy slouží jako obecné typy. C++ neumožňuje parametry šablony.  
  
-   Jazyk C++ umožňuje kód, který nemusí platit pro všechny parametry typu v šabloně, která se pak kontroluje u konkrétní typ použitý jako parametr typu. C# vyžaduje kód ve třídě má být zapsán tak, že bude fungovat s jakýmkoli typem, který splňuje omezení. Například v jazyce C++ je možné psát funkce, která používá aritmetické operátory `+` a `-` u objektů parametru typu, který vygeneruje chybu v době vytváření instancí šablony s typem, který nepodporuje tyto operátory. C# zakazuje pouze jazykové konstrukce povolené jsou ty, které je možné odvodit z omezení.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [Šablony](/cpp/cpp/templates-cpp)
