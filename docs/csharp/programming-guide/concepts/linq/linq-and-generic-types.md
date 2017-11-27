---
title: "LINQ a obecné typy (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e62a1573fa5ebf51a5f0f23b133c274730cfbeb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linq-and-generic-types-c"></a>LINQ a obecné typy (C#)
[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]dotazy jsou založeny na obecné typy, které zavedených ve verzi 2.0 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Před zahájením zápis dotazů nepotřebujete důkladné znalosti jazyka obecné typy. Můžete ale chtít pochopit dvě základní koncepty:  
  
1.  Při vytváření instance třídy obecnou kolekci jako <xref:System.Collections.Generic.List%601>, typ objektů, které bude obsahovat seznam je nahradit "T". Například je seznam řetězců, vyjádřené jako `List<string>`a seznam `Customer` objektů je vyjádřen jako `List<Customer>`. Seznam Obecné je silného typu a poskytuje mnoho výhod oproti kolekce, které ukládají jejich elementů jako <xref:System.Object>. Pokud se pokusíte přidat `Customer` k `List<string>`, zobrazí se chyba při kompilaci. Protože není nutné provádět typ přetypování běhu je snadno použitelný obecné kolekce.  
  
2.  <xref:System.Collections.Generic.IEnumerable%601>je rozhraní, které umožňuje obecnou kolekci třídy výčet pomocí `foreach` příkaz. Obecné kolekce tříd podporu <xref:System.Collections.Generic.IEnumerable%601> stejně jako negenerická kolekce tříd, například <xref:System.Collections.ArrayList> podporu <xref:System.Collections.IEnumerable>.  
  
 Další informace o obecných typech najdete v tématu [obecné typy](../../../../csharp/programming-guide/generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>Rozhraní IEnumerable < T\> proměnné v dotazech LINQ  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]proměnné dotazu jsou zadány jako <xref:System.Collections.Generic.IEnumerable%601> nebo odvozený typ jako <xref:System.Linq.IQueryable%601>. Až se zobrazí proměnné dotazu, který je zadán jako `IEnumerable<Customer>`, právě znamená, že dotaz, když je proveden, vytvoří posloupnost nula nebo více `Customer` objekty.  
  
 [!code-csharp[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]  
  
 Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Když necháte deklarace kompilátoru popisovač obecného typu  
 Pokud dáváte přednost, se můžete vyhnout Obecná syntaxe pomocí [var](../../../../csharp/language-reference/keywords/var.md) – klíčové slovo. `var` – Klíčové slovo instruuje kompilátor, aby odvození typu proměnné dotazu pohledem na zdroj dat uvedený v `from` klauzule. Následující příklad vytvoří stejný zkompilovaný kód jako v předchozím příkladu:  
  
 [!code-csharp[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]  
  
 `var` – Klíčové slovo je užitečné, pokud je typ proměnné zřejmé nebo když není to důležité k explicitnímu zadání vnořené obecné typy, jako jsou ty, které vytváří skupiny dotazy. Obecně platí, doporučujeme, pokud používáte `var`, uvědomte si, že ho může ztížit kódu pro ostatní uživatele. Další informace najdete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s dotazy LINQ v jazyku C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Obecné typy](../../../../csharp/programming-guide/generics/index.md)
