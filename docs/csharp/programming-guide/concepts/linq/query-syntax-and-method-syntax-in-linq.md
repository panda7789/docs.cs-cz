---
title: Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 17280daaf98010245bbd019652a2a46d7f66ab59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635493"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)
Většina dotazů v dokumentaci integrovaného dotazu zaváděcího jazyka (LINQ) je napsána pomocí syntaxe deklarativního dotazu LINQ. Syntaxe dotazu však musí být přeložena do volání metody pro běh .NET common language runtime (CLR) při kompilaci kódu. Tato volání metod vyvolávají standardní operátory dotazů, `Join`které `Max`mají `Average`názvy , například `Where`, `Select` `GroupBy`, , a . Můžete volat přímo pomocí syntaxe metody namísto syntaxe dotazu.  
  
 Syntaxe a syntaxe metody dotazu jsou sémanticky identické, ale mnoho lidí považuje syntaxi dotazu za jednodušší a čitelnější. Některé dotazy musí být vyjádřeny jako volání metody. Například je nutné použít volání metody vyjádřit dotaz, který načte počet prvků, které odpovídají zadané podmínce. Musíte také použít volání metody pro dotaz, který načte prvek, který má maximální hodnotu ve zdrojové sekvenci. Referenční dokumentace pro standardní operátory <xref:System.Linq> dotazů v oboru názvů obvykle používá syntaxi metody. Proto i při začínání psaní linq dotazů, je užitečné být obeznámeni s tím, jak používat syntaxi metody v dotazech a ve výrazech dotazu sami.  
  
## <a name="standard-query-operator-extension-methods"></a>Metody rozšíření standardních operátorů dotazů  
 Následující příklad ukazuje jednoduchý *výraz dotazu* a sémanticky ekvivalentní dotaz napsaný jako *dotaz založený na metodě*.  
  
 [!code-csharp[csLINQGettingStarted#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#22)]  
  
 Výstup z obou příkladů je identický. Můžete vidět, že typ proměnné dotazu je stejný <xref:System.Collections.Generic.IEnumerable%601>v obou formách: .  
  
 Chcete-li porozumět dotazu založenému na metodě, podívejme se na něj podrobněji. Na pravé straně výrazu všimněte `where` si, že klauzule je `numbers` nyní vyjádřena jako metoda instance `IEnumerable<int>`na objektu, který, jak si budete vzpomenout, má typ . Pokud jste obeznámeni <xref:System.Collections.Generic.IEnumerable%601> s obecným rozhraním, víte, že nemá metodu. `Where` Pokud však vyvoláte seznam dokončení technologie IntelliSense v ide sady `Where` Visual Studio, zobrazí `Select`se `SelectMany` `Join`nejen `Orderby`metoda, ale také mnoho dalších metod, například , , a . Jedná se o všechny standardní operátory dotazu.  
  
 ![Snímek obrazovky zobrazující všechny standardní operátory dotazů v aplikaci Intellisense](./media/query-syntax-and-method-syntax-in-linq/standard-query-operators.png)  
  
 I když to <xref:System.Collections.Generic.IEnumerable%601> vypadá, jako by byl předefinován tak, aby zahrnovala tyto další metody, ve skutečnosti tomu tak není. Standardní operátory dotazů jsou implementovány jako nový druh metody nazývané *metody rozšíření*. Rozšíření metody "rozšířit" existující typ; mohou být volány, jako by byly instance metody na typu. Standardní operátory <xref:System.Collections.Generic.IEnumerable%601> dotazů rozšířit a `numbers.Where(...)`to je důvod, proč můžete psát .  
  
 Chcete-li začít používat LINQ, vše, co opravdu potřebujete vědět o metodách rozšíření je, jak je přenést do oboru ve vaší aplikaci pomocí správné `using` direktivy. Z hlediska aplikace rozšíření metody a metody pravidelné instance jsou stejné.  
  
 Další informace o metodách rozšíření naleznete v [tématu Extension Methods](../../classes-and-structs/extension-methods.md). Další informace o standardních operátorech dotazů naleznete v [tématu Přehled standardních operátorů dotazů (C#).](./standard-query-operators-overview.md) Někteří zprostředkovatelé LINQ, například [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], implementovat své vlastní <xref:System.Collections.Generic.IEnumerable%601>operátory standardní dotaz a další metody rozšíření pro jiné typy kromě .  
  
## <a name="lambda-expressions"></a>Lambda – výrazy  
 V předchozím příkladu všimněte si, že podmíněný výraz (`num % 2 == 0`) `Where` je `Where(num => num % 2 == 0).` předán jako in-line argument metody: Tento vložký výraz se nazývá výraz lambda. Je to pohodlný způsob, jak napsat kód, který by jinak musel být napsán v těžkopádnější formě jako anonymní metoda nebo obecný delegát nebo strom výrazů. V C# `=>` je lambda operátor, který se čte jako "přejde do". Vlevo `num` od operátoru je vstupní proměnná, `num` která odpovídá ve výrazu dotazu. Kompilátor může odvodit `num` typ, `numbers` protože <xref:System.Collections.Generic.IEnumerable%601> ví, že je obecný typ. Tělo lambda je stejný jako výraz v syntaxi dotazu nebo v jiném c# výraz nebo příkaz; může zahrnovat volání metod a další komplexní logiku. "Vrácená hodnota" je pouze výsledek výrazu.  
  
 Chcete-li začít používat LINQ, není nutné používat lambdas značně. Některé dotazy však mohou být vyjádřeny pouze v syntaxi metody a některé z nich vyžadují výrazy lambda. Poté, co se více seznámíte s lambdy, zjistíte, že jsou výkonným a flexibilním nástrojem v krabici nástrojů LINQ. Další informace naleznete v tématu [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Skládání dotazů  
 V předchozím příkladu kódu `OrderBy` si všimněte, že metoda je vyvolána `Where`pomocí operátoru tečky při volání . `Where`vytvoří filtrovanou sekvenci a pak `Orderby` pracuje na této sekvenci řazením. Vzhledem k `IEnumerable`tomu, že dotazy vrátí , můžete je sestavit v syntaxi metody zřetězením volání metody dohromady. To je to, co kompilátor dělá na pozadí při psaní dotazů pomocí syntaxe dotazu. A protože proměnná dotazu neukládá výsledky dotazu, můžete ji upravit nebo použít jako základ pro nový dotaz kdykoli, i po jeho spuštění.  
