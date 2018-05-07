---
title: Zprostředkovatelé typů
description: 'Zjistěte, jak poskytovatele typu F # je komponenta, která poskytuje typy, vlastnosti a metody pro použití ve vašich aplikacích.'
ms.date: 04/02/2018
ms.openlocfilehash: 82d9afed7d77eae5f8b96854d40e96a32c4fae9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="type-providers"></a>Zprostředkovatelé typů

Poskytovatel typů jazyka F# je komponenta, která poskytuje typy, vlastnosti a metody pro váš program. Zprostředkovatelé typů generovat, co se označují jako **zadané typy**, které jsou generovány nástrojem kompilátor jazyka F # a jsou založené na externí zdroj dat.

F # typ poskytovatele SQL můžete například vygenerovat typy reprezentující tabulky a sloupce v relační databázi. Ve skutečnosti se jedná, co [SQLProvider](https://fsprojects.github.io/SQLProvider/) nemá typ poskytovatele.

Pokud že typy závisí na vstupní parametry pro zprostředkovatele typů. Takové vstup může být ukázkového zdroje dat (například soubor schématu JSON), adresu URL přejdete přímo na externí službu nebo řetězec připojení ke zdroji dat. Typ zprostředkovatele můžete také zajistit, že skupiny typy jsou pouze rozšířit na vyžádání; To znamená jsou rozšířit Pokud typy jsou ve skutečnosti odkazuje vašeho programu. To umožňuje přímou integraci rozsáhlých informačních prostorů přístupných na vyžádání, jako jsou například online datové trhy, způsobem využívajícím silné typy.

## <a name="generative-and-erased-type-providers"></a>Zprostředkovatelé typů tvoří a vymazaných

Zprostředkovatelé typů pocházejí ve dvou formách: tvoří a vymazaných.

Tvoří zprostředkovatelů typů vytvořit typy, které se dají zapsat jako typy .NET do sestavení, ve kterém se vytváří. To umožňuje, aby z kódu v ostatních sestavení využívat. To znamená, že reprezentaci typu zdroje dat musí obecně být ten, který je vhodný k reprezentaci s typy .NET.

Mazání zprostředkovatelů typů vytvořit typy, které mohou být využívány pouze v sestavení nebo projektu, který se generují z. Typy jsou dočasné; To znamená nejsou zapsány do sestavení a nemůže být využívány službou kódu v ostatních sestavení. Mohou obsahovat *odložené* členy, umožní vám použití zadané typy z prostoru potenciálně nekonečné informace. Jsou užitečné pro používání malou část zdroje dat velké a vzájemně propojena.

## <a name="commonly-used-type-providers"></a>Běžně používané zprostředkovatelů typů

Následující knihovny nejběžněji používané obsahovat typ zprostředkovatele pro jiné účely:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) obsahuje typ zprostředkovatele pro JSON, XML, CSV a HTML dokumentu formáty a prostředky.
- [SQLProvider](https://fsprojects.github.io/SQLProvider/) poskytuje dotazy pro tyto zdroje dat silného typu přístup k databázím vztah prostřednictvím objektu mapování a F # LINQ.
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) má sadu typ zprostředkovatele pro kompilaci zaškrtnutí vložení T-SQL v jazyce F #.
- [Zprostředkovatel Azure typ úložiště](https://fsprojects.github.io/AzureStorageTypeProvider/) obsahuje typy pro Azure BLOB, tabulek a front, což umožňuje přístup k těmto prostředkům, aniž by museli zadat názvy prostředků jako řetězce v rámci vašeho programu.
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) obsahuje **GraphQLProvider**, který obsahuje typy podle GraphQL server určený adresy URL.

V případě potřeby můžete [vytvořit vlastní zprostředkovatele vlastního typu](creating-a-type-provider.md), nebo zadejte odkaz na typ zprostředkovatele, které byly vytvořeny třetími stranami. Předpokládejme například organizaci, která má datovou službu poskytující velké a zvyšující se množství pojmenovaných datových sad, přičemž každá z nich má vlastní stabilní schéma dat. Můžete vytvořit poskytovatele typů, který schémata přečte a nabídne programátorům nejnovější dostupné datové sady se silnými typy.

## <a name="see-also"></a>Viz také
[Kurz: Vytvoření zprostředkovatele typů](creating-a-type-provider.md)

[Referenční dokumentace jazyka F#](../../language-reference/index.md)

[Visual F#](../../index.md)
