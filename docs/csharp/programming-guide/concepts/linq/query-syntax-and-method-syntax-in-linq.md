---
title: "Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0127ee0815c4ba6a697456fe45bd373bcf9ba4e4
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)
Většina dotazů v úvodní integrované Query Language ([!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]) dokumentace jsou zapsány pomocí syntaxe deklarativní dotazu LINQ. Syntaxe dotazu je však přeložit do volání metod pro rozhraní .NET common language runtime (CLR), při kompilaci kódu. Tato metoda volání vyvolají standardní operátory dotazu, které mají názvy jako `Where`, `Select`, `GroupBy`, `Join`, `Max`, a `Average`. Můžete je volat přímo pomocí syntaxe využívající metody místo syntaxe dotazu.  
  
 Syntaxe dotazu a syntaxe využívající metody jsou sémanticky identické, ale Spousta lidí najít syntaxe dotazů jednodušší a snadněji číst. Některé dotazy musí být vyjádřena jako volání metody. Například musíte použít volání metody vyjádřit dotaz, který načte počet elementů, které splňují zadanou podmínku. Volání metody musíte použít také pro dotaz, který načte elementu, který má maximální hodnota ve zdrojové sekvence. Referenční dokumentaci k nástroji standardní operátory dotazu v <xref:System.Linq> obor názvů se obvykle používá metoda syntaxe. Proto i v případě Začínáme zápis [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, je vhodné se seznámit s použití syntaxe využívající metody v dotazech a ve výrazech dotazů sami.  
  
## <a name="standard-query-operator-extension-methods"></a>Metody rozšíření standardních operátorů dotazů  
 Následující příklad ukazuje jednoduchý *dotaz výrazu* a sémanticky ekvivalentní dotaz zapisují jako *dotaz založený na metoda*.  
  
 [!code-csharp[csLINQGettingStarted#22](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/query-syntax-and-method-syntax-in-linq_1.cs)]  
  
 Výstup z uvedených dvou příkladech se shoduje. Uvidíte, že typ proměnné v dotazu je stejná v obou forms: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Zjistit dotaz na základě metod Podívejme se na jeho přesněji. Na pravé straně výrazu, Všimněte si, že `where` klauzule teď vyjádřený jako metodu instance na `numbers` má typ objektu, který jako vám bude odvolat `IEnumerable<int>`. Pokud jste se seznámili s Obecná <xref:System.Collections.Generic.IEnumerable%601> rozhraní, víte, že nemá `Where` metoda. Ale pokud vyvolání seznamu dokončení IntelliSense v prostředí Visual Studio IDE, zobrazí se jenom `Where` metoda, ale jiné metody, jako `Select`, `SelectMany`, `Join`, a `Orderby`. Toto jsou všechny standardní operátory dotazu.  
  
 ![Standardní operátory dotazu v Intellisense](../../../../csharp/programming-guide/concepts/linq/media/standardqueryops.png "StandardQueryOps")  
  
 I když vypadá to, jako kdyby <xref:System.Collections.Generic.IEnumerable%601> podřízených zahrnout tyto další metody fakt tomu tak není. Standardní operátory dotazu jsou implementované jako nový druh metodu s názvem *rozšiřující metody*. Metody rozšíření "rozšíření" existující typ; je možné volat jako kdyby byly metody instance typu. Rozšíření standardní operátory dotazu <xref:System.Collections.Generic.IEnumerable%601> a který je proč můžete napsat `numbers.Where(...)`.  
  
 Abyste mohli začít používat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], všechno, co máte skutečně potřebujete vědět o rozšiřující metody je postup, aby byly v oboru ve vaší aplikaci pomocí správného `using` direktivy. Z vaší aplikace metody rozšíření a normální instanci metody jsou stejné.  
  
 Další informace o metodách rozšíření najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Další informace o standardních operátorů dotazu najdete v tématu [standardní přehled operátory dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md). Některé [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatelů, jako například [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], implementovat vlastní standardní operátory dotazu a další rozšiřující metody pro jiné typy kromě <xref:System.Collections.Generic.IEnumerable%601>.  
  
## <a name="lambda-expressions"></a>Výrazy lambda  
 V předchozím příkladu, Všimněte si, že podmíněným výrazem (`num % 2 == 0`) se předá jako argumentu v řádku `Where` metoda: `Where(num => num % 2 == 0).` tento výraz vložené nazývá výrazu lambda. Je pohodlný způsob, jak napsat kód, který byste jinak museli k zapsání v těžkopádnější formuláře jako anonymní metody nebo obecný delegát strom výrazu se nezdařilo. V jazyce C# `=>` je lambda operátor, který je pro čtení jako "vloží do". `num` Na levé straně operátoru je vstupní proměnné, který odpovídá `num` ve výrazu dotazu. Kompilátor lze odvodit typ `num` vzhledem k tomu, který zná `numbers` je obecný <xref:System.Collections.Generic.IEnumerable%601> typu. Tělo argument lambda je stejně jako výraz v syntaxi dotazu nebo v jakékoli jiné C# výraz nebo příkaz; může zahrnovat volání metod a jiné komplexní logiku. "Návratovou hodnotu" je právě výsledkem výrazu.  
  
 Abyste mohli začít používat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], není nutné používat lambdas hojně. Ale některé dotazy lze vyjádřit pouze v syntaxe využívající metody a některé z nich vyžadovat výrazy lambda. Po seznámení s lambdas, zjistíte, že jsou nástroje výkonný a flexibilní vaší [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sady nástrojů. Další informace najdete v tématu [výrazy Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Skládání dotazů  
 V předchozím příkladu kódu, Všimněte si, že `OrderBy` metoda je volána pomocí operátoru tečka na volání `Where`. `Where`Vytvoří filtrované pořadí a potom `Orderby` funguje v tomto pořadí tak, že ho řazení. Protože vrátit dotazy `IEnumerable`, můžete vytvořit v syntaxi metoda podle řetězení volání metod společně. Toto je kompilátor jaké na pozadí při psaní dotazy pomocí syntaxe dotazu. A protože proměnné dotazu neukládá výsledky dotazu, můžete upravit ji nebo ji použít jako základ pro nový dotaz kdykoli, i když nebyla spuštěna.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s dotazy LINQ v jazyku C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
