---
title: Implicitně typované lokální proměnné - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 68c0ff055c91f4f1deca6fcfada0f14577439731
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237009"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Implicitně typované lokální proměnné (Průvodce programováním v C#)
Lokální proměnné mohou být deklarovány bez explicitního typu. `var` – Klíčové slovo instruuje kompilátor k odvození typu proměnné z výrazu na pravé straně výrazu inicializace. Odvozený typ může být předdefinovaný typ, anonymního typu, uživatelem definovaný typ nebo typ definovaný v knihovně tříd rozhraní .NET Framework. Další informace o tom, jak inicializovat pole s `var`, naleznete v tématu [implicitně typované pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
 Následující příklady znázorňují různé způsoby, jimiž lze deklarovat lokální proměnné s `var`:  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 Je důležité si uvědomit, že `var` – klíčové slovo neznamená "varianta" a neznamená, že proměnná je volně typem nebo s pozdní vazbou. Znamená pouze to, že kompilátor zjistí a přiřadí nejvhodnější typ.  
  
 `var` – Klíčové slovo lze použít v následujících kontextů:  
  
-   Na lokální proměnné (proměnné deklarované v oboru metoda) jak je znázorněno v předchozím příkladu.  
  
-   V [pro](../../../csharp/language-reference/keywords/for.md) příkaz inicializace.  
  
    ```csharp  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   V [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz inicializace.  
  
    ```csharp  
    foreach(var item in list){...}  
    ```  
  
-   V [pomocí](../../../csharp/language-reference/keywords/using-statement.md) příkazu.  
  
    ```csharp  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 Další informace najdete v tématu [jak: Použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).  
  
## <a name="var-and-anonymous-types"></a>var a anonymní typy  
 V mnoha případech použití `var` je volitelný a je právě syntaktické pohodlí. Ale když proměnná je inicializována pomocí anonymního typu je třeba deklarovat jako proměnnou `var` Pokud potřebujete přístup k vlastnostem objektu později. Toto je běžný scénář v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů. Další informace najdete v tématu [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Z hlediska zdrojového kódu anonymního typu nemá žádný název. Proto pokud proměnné dotazu byl inicializován s `var`, je jediný způsob, jak přistupovat k vlastnosti ve vrácené posloupnosti objekty používat `var` jako typ proměnné iterace ve `foreach` příkazu.  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a>Poznámky  
 Implicitně typované proměnné deklaracích platí následující omezení:  
  
-   `var` jde použít jenom při místní proměnné je deklarovat a inicializovat ve stejném příkazu; proměnnou nejde inicializovat na null nebo na skupinu metod nebo anonymní funkce.  
  
-   `var` nelze použít na pole v oboru třídy.  
  
-   Proměnné deklarované s použitím `var` nelze použít ve výrazu inicializace. Jinými slovy, tento výraz je právní`: int i = (i = 20);` , ale tento výraz způsobí chybu kompilace: `var i = (i = 20);`  
  
-   Více implicitně typované proměnné nelze inicializovat ve stejném příkazu.  
  
-   Pokud typ s názvem `var` je v oboru, pak bude `var` – klíčové slovo se přeloží název tohoto typu a se nezpracuje jako součást implicitně typované lokální proměnné deklarace.  
  
 Možná zjistíte, `var` může být také užitečný v případě výrazy dotazů, ve kterých je obtížné určit přesné konstruovaný typ proměnné dotazu. Tato situace může nastat s seskupování a řazení operace.  
  
 `var` – Klíčové slovo může být také užitečné, když konkrétní typ proměnné je únavné pro psaní na klávesnici, nebo je zřejmé nebo nepřidá do čitelnost kódu. Jedním z příkladů kde `var` je užitečné v tomto způsob je pomocí vnořených obecných typech, jako jsou ty používané s operacemi skupiny. V následující dotaz, je typ proměnné dotazu `IEnumerable<IGrouping<string, Student>>`. Za předpokladu, můžete vy a ostatní, kteří musí udržovat váš kód pochopit, neexistuje žádný problém s použitím implicitního zápisu pro usnadnění práce a zkrácení.  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 Nicméně použití `var` mohou mít alespoň potenciálně ztížit váš kód pochopit pro jiné vývojáře. Z tohoto důvodu dokumentace jazyka C# obecně používá `var` pouze pokud je povinný.  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Implicitně typovaná pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
- [Postupy: Použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
- [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [var](../../../csharp/language-reference/keywords/var.md)  
- [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [LINQ (Language-Integrated Query)](../../../csharp/linq/index.md)  
- [for](../../../csharp/language-reference/keywords/for.md)  
- [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
- [using – příkaz](../../../csharp/language-reference/keywords/using-statement.md)
