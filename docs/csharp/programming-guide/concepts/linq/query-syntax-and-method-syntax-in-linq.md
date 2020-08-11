---
title: Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)
description: Seznamte se s syntaxí dotazů a syntaxí metod v LINQ. Patří sem standardní metody rozšíření operátoru dotazu a výrazy lambda.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 46b0e44182d22158aa5fa54a0f44bae70aa8ddd9
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063039"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)
Většina dotazů v dokumentaci k úvodnímu jazyku (LINQ) je zapsána pomocí syntaxe deklarativního dotazu LINQ. Nicméně syntaxe dotazu musí být přeložena do volání metody pro modul CLR (Common Language Runtime) .NET, když je kód zkompilován. Tyto volání metod vyvolávají standardní operátory dotazu, které mají názvy jako `Where` , `Select` , `GroupBy` , `Join` , `Max` a `Average` . Můžete je volat přímo pomocí syntaxe metody namísto syntaxe dotazu.  
  
 Syntaxe dotazu a syntaxe metody jsou sémanticky identické, ale mnoho lidí nalezne syntax dotazů jednodušší a snazší pro čtení. Některé dotazy musí být vyjádřeny jako volání metody. Například je nutné použít volání metody k vyjádření dotazu, který načte počet prvků, které odpovídají zadané podmínce. Také je nutné použít volání metody pro dotaz, který načte prvek, který má maximální hodnotu ve zdrojové sekvenci. Referenční dokumentace pro standardní operátory dotazů v <xref:System.Linq> oboru názvů obecně používá syntaxi metody. Proto, i když Začínáme s psaním dotazů LINQ, je vhodné se seznámit s tím, jak používat syntaxi metody v dotazech a ve výrazech dotazů samotných.  
  
## <a name="standard-query-operator-extension-methods"></a>Metody rozšíření standardních operátorů dotazů  
 Následující příklad ukazuje jednoduchý *výraz dotazu* a sémanticky ekvivalentní dotaz zapsaný jako *dotaz založený na metodě*.  
  
 [!code-csharp[csLINQGettingStarted#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#22)]  
  
 Výstup ze dvou příkladů je stejný. Můžete vidět, že typ proměnné dotazu je stejný v obou formulářích: <xref:System.Collections.Generic.IEnumerable%601> .  
  
 Abychom porozuměli dotazům založeným na metodách, Podívejme se na to podrobněji. Na pravé straně výrazu si všimněte, že `where` klauzule je nyní vyjádřena jako metoda instance `numbers` objektu, což znamená, že navrácení má typ `IEnumerable<int>` . Pokud jste obeznámeni s obecným <xref:System.Collections.Generic.IEnumerable%601> rozhraním, víte, že nemá `Where` metodu. Nicméně pokud vyvoláte seznam dokončení IntelliSense v integrovaném vývojovém prostředí sady Visual Studio, zobrazí se nejenom `Where` metoda, ale spousta dalších metod, jako `Select` je,, `SelectMany` `Join` a `Orderby` . Jedná se o všechny standardní operátory dotazu.  
  
 ![Snímek obrazovky znázorňující všechny standardní operátory dotazu v IntelliSense](./media/query-syntax-and-method-syntax-in-linq/standard-query-operators.png)  
  
 I když se zdá, že <xref:System.Collections.Generic.IEnumerable%601> se předefinoval, aby zahrnoval tyto další metody, ve skutečnosti to není případ. Standardní operátory dotazu jsou implementovány jako nový typ metody s názvem *rozšiřující metody*. Rozšiřující metody "extend" existující typ; mohou být volány, jako by šlo o metody instance pro daný typ. Standardní operátory dotazu přesahují <xref:System.Collections.Generic.IEnumerable%601> a, což je důvod, proč můžete zapisovat `numbers.Where(...)` .  
  
 Chcete-li začít používat LINQ, vše, co opravdu potřebujete znát o metodách rozšíření, je způsob, jak je přenést do rozsahu aplikace pomocí správných `using` direktiv. Z pohledu vaší aplikace je metoda rozšíření a pravidelná metoda instance stejná.  
  
 Další informace o metodách rozšíření naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md). Další informace o standardních operátorech dotazů naleznete v tématu [Přehled standardních operátorů dotazu (C#)](./standard-query-operators-overview.md). Někteří poskytovatelé LINQ, například [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , implementují své vlastní standardní operátory dotazování a další metody rozšíření pro jiné typy kromě <xref:System.Collections.Generic.IEnumerable%601> .  
  
## <a name="lambda-expressions"></a>Lambda – výrazy  
 V předchozím příkladu si všimněte, že podmíněný výraz ( `num % 2 == 0` ) je předán jako do vloženého argumentu `Where` metody: `Where(num => num % 2 == 0).` Tento vložený výraz se nazývá výraz lambda. Je pohodlný způsob, jak napsat kód, který by jinak musel být napsán ve složitější formě jako anonymní metoda nebo jako obecný delegát nebo strom výrazu. V jazyce C# `=>` je operátor lambda, který je čten jako "Přejít na". Na `num` levé straně operátoru je vstupní proměnná, která odpovídá `num` výrazu dotazu. Kompilátor může odvodit typ `num` , protože ví, že `numbers` se jedná o obecný <xref:System.Collections.Generic.IEnumerable%601> typ. Tělo lambda je pouze stejné jako výraz v syntaxi dotazu nebo v jakémkoli jiném výrazu jazyka C# nebo příkazu; může zahrnovat volání metod a další komplexní logiku. "Návratovou hodnotou" je pouze výsledek výrazu.  
  
 Chcete-li začít používat LINQ, nemusíte často používat výrazy lambda. Nicméně některé dotazy lze vyjádřit pouze v syntaxi metody a některé z nich vyžadují výrazy lambda. Po podrobnějším seznámení s výrazy lambda zjistíte, že jsou výkonným a flexibilním nástrojem v sadě LINQ Toolbox. Další informace naleznete v tématu [lambda výrazy](../../../language-reference/operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Skládání dotazů  
 V předchozím příkladu kódu si všimněte, že `OrderBy` Metoda je vyvolána pomocí operátoru tečka v volání `Where` . `Where`Vytvoří filtrovanou sekvenci a potom `Orderby` v této sekvenci funguje tak, že ji seřadí. Vzhledem k tomu, že dotazy vrátí `IEnumerable` , je vytvoříte v syntaxi metody zřetězením volání metody dohromady. To je to, co kompilátor provede na pozadí při psaní dotazů pomocí syntaxe dotazů. A protože proměnná dotazu neukládá výsledky dotazu, můžete ji upravit nebo použít jako základ pro nový dotaz kdykoli, a to i po provedení.  
