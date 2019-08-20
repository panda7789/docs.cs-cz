---
title: Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 8351661bdb7eaf841577eb128a8fec12efed2360
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591419"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)
Většina dotazů v úvodní dokumentaci k základnímu jazyku ([!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]) je zapsána pomocí syntaxe deklarativního dotazu LINQ. Nicméně syntaxe dotazu musí být přeložena do volání metody pro modul CLR (Common Language Runtime) .NET, když je kód zkompilován. Tyto volání metod vyvolávají standardní operátory dotazu `Where`, které mají názvy jako, `Select`, `GroupBy`, `Join`, `Max`a `Average`. Můžete je volat přímo pomocí syntaxe metody namísto syntaxe dotazu.  
  
 Syntaxe dotazu a syntaxe metody jsou sémanticky identické, ale mnoho lidí nalezne syntax dotazů jednodušší a snazší pro čtení. Některé dotazy musí být vyjádřeny jako volání metody. Například je nutné použít volání metody k vyjádření dotazu, který načte počet prvků, které odpovídají zadané podmínce. Také je nutné použít volání metody pro dotaz, který načte prvek, který má maximální hodnotu ve zdrojové sekvenci. Referenční dokumentace pro standardní operátory dotazů v <xref:System.Linq> oboru názvů obecně používá syntaxi metody. Proto, i když Začínáme s psaním [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů, je vhodné se seznámit s tím, jak používat syntaxi metody v dotazech a ve výrazech dotazů.  
  
## <a name="standard-query-operator-extension-methods"></a>Metody rozšíření standardních operátorů dotazů  
 Následující příklad ukazuje jednoduchý *výraz dotazu* a sémanticky ekvivalentní dotaz zapsaný jako *dotaz založený na metodě*.  
  
 [!code-csharp[csLINQGettingStarted#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#22)]  
  
 Výstup ze dvou příkladů je stejný. Můžete vidět, že typ proměnné dotazu je stejný v obou formulářích: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Abychom porozuměli dotazům založeným na metodách, Podívejme se na to podrobněji. Na pravé straně výrazu si všimněte, že `where` klauzule je nyní vyjádřena jako metoda `numbers` instance objektu, což znamená, že `IEnumerable<int>`navrácení má typ. Pokud jste obeznámeni s obecným <xref:System.Collections.Generic.IEnumerable%601> rozhraním, víte, že `Where` nemá metodu. Nicméně pokud vyvoláte seznam dokončení IntelliSense v integrovaném vývojovém prostředí `Where` sady Visual Studio, zobrazí se nejenom metoda, ale spousta dalších metod `Select`, jako je, `Orderby` `SelectMany` `Join`, a. Jedná se o všechny standardní operátory dotazu.  
  
 ![Snímek obrazovky znázorňující všechny standardní operátory dotazu v IntelliSense](./media/query-syntax-and-method-syntax-in-linq/standard-query-operators.png)  
  
 I když se zdá <xref:System.Collections.Generic.IEnumerable%601> , že se předefinoval, aby zahrnoval tyto další metody, ve skutečnosti to není případ. Standardní operátory dotazu jsou implementovány jako nový typ metody s názvem *rozšiřující metody*. Rozšiřující metody "extend" existující typ; mohou být volány, jako by šlo o metody instance pro daný typ. Standardní operátory dotazu přesahují <xref:System.Collections.Generic.IEnumerable%601> a, což je důvod, proč můžete zapisovat. `numbers.Where(...)`  
  
 Chcete-li začít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]používat, stačí, když opravdu potřebujete znát o metodách rozšíření, jak je přenést do rozsahu aplikace pomocí správných `using` direktiv. Z pohledu vaší aplikace je metoda rozšíření a pravidelná metoda instance stejná.  
  
 Další informace o metodách rozšíření naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md). Další informace o standardních operátorech dotazu najdete v tématu [Přehled standardních operátorůC#dotazů ()](./standard-query-operators-overview.md). Někteří [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatelé, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] například a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], implementují své vlastní standardní operátory dotazování a další metody rozšíření pro jiné <xref:System.Collections.Generic.IEnumerable%601>typy kromě.  
  
## <a name="lambda-expressions"></a>Lambda – výrazy  
 V předchozím příkladu si všimněte, že podmíněný výraz (`num % 2 == 0`) je předán jako do vloženého argumentu `Where` metody: `Where(num => num % 2 == 0).`Tento vložený výraz se nazývá výraz lambda. Je pohodlný způsob, jak napsat kód, který by jinak musel být napsán ve složitější formě jako anonymní metoda nebo jako obecný delegát nebo strom výrazu. C# V`=>` je operátor lambda, který je čten jako "Přejít na". Na levé straně operátoru je vstupní proměnná, která odpovídá `num` výrazu dotazu. `num` Kompilátor může odvodit typ `num` , protože ví, že `numbers` se jedná o obecný <xref:System.Collections.Generic.IEnumerable%601> typ. Tělo lambda je pouze stejné jako výraz v syntaxi dotazu nebo v jakémkoli jiném C# výrazu nebo příkazu; může zahrnovat volání metod a další komplexní logiku. "Návratovou hodnotou" je pouze výsledek výrazu.  
  
 Chcete-li začít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]používat, nemusíte často používat výrazy lambda. Nicméně některé dotazy lze vyjádřit pouze v syntaxi metody a některé z nich vyžadují výrazy lambda. Až budete s výrazy lambda obeznámeni podrobněji, zjistíte, že jsou výkonným a flexibilním nástrojem v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sadě nástrojů. Další informace naleznete v tématu [lambda výrazy](../../statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Skládání dotazů  
 V předchozím příkladu kódu si všimněte, že `OrderBy` metoda je vyvolána pomocí operátoru tečka v `Where`volání. `Where`Vytvoří filtrovanou sekvenci a potom `Orderby` v této sekvenci funguje tak, že ji seřadí. Vzhledem k tomu `IEnumerable`, že dotazy vrátí, je vytvoříte v syntaxi metody zřetězením volání metody dohromady. To je to, co kompilátor provede na pozadí při psaní dotazů pomocí syntaxe dotazů. A protože proměnná dotazu neukládá výsledky dotazu, můžete ji upravit nebo použít jako základ pro nový dotaz kdykoli, a to i po provedení.  
