---
title: Implicitně typované lokální proměnné (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: c6c2bae39764e78fad2510bbc8937b0ac790bef5
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Implicitně typované lokální proměnné (Průvodce programováním v C#)
Lokální proměnné lze deklarovat bez nutnosti poskytnutí explicitního typu. `var` – Klíčové slovo instruuje kompilátor, aby odvození typu proměnné z výrazu na pravé straně příkazu inicializace. Odvozené typ může být předdefinovaný typ, anonymní typ, uživatelem definovaný typ nebo typem definovaným v knihovně tříd rozhraní .NET Framework. Další informace o tom, jak inicializovat pole s `var`, najdete v části [implicitně typované pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
 Následující příklady ukazují různé způsoby, ve kterých mohou být místní proměnné deklarovány s `var`:  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 Je důležité pochopit, že `var` – klíčové slovo neznamená "variantou" a neindikuje volně je proměnná typu nebo pozdní vazbu. Právě znamená, že kompilátor určí a přiřadí nejvhodnější typ.  
  
 `var` – Klíčové slovo je možné použít následující kontexty:  
  
-   Na lokální proměnné (proměnných deklarovaných v oboru metoda) jako v předchozím příkladu.  
  
-   V [pro](../../../csharp/language-reference/keywords/for.md) příkaz inicializace.  
  
    ```csharp  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   V [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz inicializace.  
  
    ```csharp  
    foreach(var item in list){...}  
    ```  
  
-   V [pomocí](../../../csharp/language-reference/keywords/using-statement.md) příkaz.  
  
    ```csharp  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 Další informace najdete v tématu [postupy: použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).  
  
## <a name="var-and-anonymous-types"></a>var a anonymní typy  
 V mnoha případech použití `var` je volitelný a je právě syntaktické pohodlí. Ale pokud proměnnou je inicializována s anonymní typ musíte deklarovat proměnnou jako `var` Pokud budete potřebovat pro přístup k vlastnosti objektu později. Toto je běžný scénář v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu výrazy. Další informace najdete v tématu [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Z hlediska zdrojového kódu anonymní typ nemá název. Proto pokud proměnnou dotazu byl inicializován s `var`, pak jedině pro přístup k vlastnostem v pořadí vrácených objektů, které se má používat `var` jako typ proměnné iterace ve `foreach` příkaz.  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a>Poznámky  
 Implicitně typované deklarace proměnných, které se vztahují následující omezení:  
  
-   `var` lze použít pouze při místní proměnné je deklarovaná a inicializovat v jednom příkazu; proměnnou nelze inicializovat na hodnotu null nebo ke skupině metoda nebo anonymní funkce.  
  
-   `var` nelze použít na pole v rozsahu třídy.  
  
-   Proměnných deklarovaných pomocí `var` nelze použít ve výrazu inicializace. Jinými slovy, je tento výraz právní`: int i = (i = 20);` , ale tento výraz způsobí chybu kompilace: `var i = (i = 20);`  
  
-   Více implicitně typované proměnné nelze inicializovat v jednom příkazu.  
  
-   Pokud název typu `var` nachází v oboru, pak se `var` – klíčové slovo bude odkazující na název tohoto typu a nebude považován za součást implicitně typovaná deklarace místní proměnné.  
  
 Můžete zjistit, že `var` může být také užitečná pro výrazy dotazů, ve kterých je obtížné určit přesnou vytvořený typ proměnné v dotazu. Tato situace může nastat s seskupování a řazení operace.  
  
 `var` – Klíčové slovo může také být užitečné při specifický typ proměnné je zdlouhavé na typ na klávesnici, nebo je zřejmé nebo nepřidá do čitelnost kódu. Jedním z příkladů kde `var` je užitečné v tomto způsobem je s vnořené obecné typy, jako jsou ty používané s operacemi skupiny. V následující dotaz, je typ proměnné dotazu `IEnumerable<IGrouping<string, Student>>`. Tak dlouho, dokud uživatelů musí zachovat kódu lepší vysvětlení, neexistuje žádný problém s použitím implicitního zadáním kvůli pohodlí a jako stručný výtah.  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 Ale použití `var` mít minimálně potenciální, aby byl váš kód více těžko srozumitelné pro ostatní vývojáři. Z tohoto důvodu dokumentace jazyka C# obecně používá `var` pouze pokud je požadovaná.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Implicitně typovaná pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [Postupy: Použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu.](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [for](../../../csharp/language-reference/keywords/for.md)  
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
 [using – příkaz](../../../csharp/language-reference/keywords/using-statement.md)
