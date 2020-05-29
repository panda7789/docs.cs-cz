---
title: Zprostředkovatelé typů
description: 'Přečtěte si, jak je poskytovatel typu F # součástí, která poskytuje typy, vlastnosti a metody pro použití ve svých programech.'
ms.date: 04/02/2018
ms.openlocfilehash: eae64d2e318ee93f0b8d5b91f0c6da6c91743527
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202114"
---
# <a name="type-providers"></a>Zprostředkovatelé typů

Poskytovatel typů jazyka F# je komponenta, která poskytuje typy, vlastnosti a metody pro váš program. Zprostředkovatelé typů generují, co jsou známé jako **poskytnuté typy**, které jsou generovány kompilátorem F # a jsou založeny na externím zdroji dat.

Například poskytovatel typů jazyka F # pro SQL může generovat typy reprezentující tabulky a sloupce v relační databázi. Ve skutečnosti to dělá poskytovatel typu [SQLProvider](https://fsprojects.github.io/SQLProvider/) .

Poskytnuté typy závisí na vstupních parametrech pro poskytovatele typu. Tento vstup může být ukázkový zdroj dat (například soubor schématu JSON), adresa URL ukazující přímo na externí službu nebo připojovací řetězec ke zdroji dat. Poskytovatel typu taky může zajistit, aby se skupiny typů rozšířily jenom na vyžádání. To znamená, že jsou rozbaleny v případě, že váš program ve skutečnosti odkazuje na typy. To umožňuje přímou integraci rozsáhlých informačních prostorů přístupných na vyžádání, jako jsou například online datové trhy, způsobem využívajícím silné typy.

## <a name="generative-and-erased-type-providers"></a>Regenerační a mazání Poskytovatelé typů

Poskytovatelé typů přicházejí ve dvou formách: regenerační a vymazáno.

Typy, které mohou být vytvořeny jako typy .NET, do sestavení, ve kterém jsou vytvářeny, poskytovatelé typů. To umožňuje, aby byly spotřebovány z kódu v jiných sestaveních. To znamená, že zadaná reprezentace zdroje dat musí být obvykle ta, která je proveditelná pro reprezentaci typů .NET.

Mazání poskytovatelů typů vytvoří typy, které lze spotřebovat pouze v sestavení nebo projektu, ze kterého jsou vygenerovány. Typy jsou dočasné; To znamená, že nejsou zapsány do sestavení a nemohou být spotřebovány kódem v jiných sestaveních. Můžou obsahovat *Zpožděné* členy, které vám umožní používat poskytnuté typy z potenciálně neomezeného informačního prostoru. Jsou užitečné pro použití malé podmnožiny velkého a propojeného zdroje dat.

## <a name="commonly-used-type-providers"></a>Běžně využívané Poskytovatelé typů

Následující široce používané knihovny obsahují poskytovatele typů pro různá použití:

- [FSharp. data](https://fsharp.github.io/FSharp.Data/) zahrnují poskytovatele typů pro formáty dokumentů JSON, XML, CSV a HTML.
- [SQLProvider](https://fsprojects.github.io/SQLProvider/) poskytuje přístup silného typu ke relačním databázím prostřednictvím mapování objektů a dotazů F # LINQ na tyto zdroje dat.
- [FSharp. data. SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) má sadu poskytovatelů typů pro kontrolované vkládání T-SQL do jazyka F # v době kompilace.
- [Zprostředkovatel typu Azure Storage](https://fsprojects.github.io/AzureStorageTypeProvider/) poskytuje typy pro objekty blob, tabulky a fronty Azure, které umožňují přístup k těmto prostředkům bez nutnosti zadávat názvy prostředků jako řetězce v celém programu.
- [FSharp. data. GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) obsahuje **GraphQLProvider**, které poskytuje typy založené na serveru GraphQL určeném adresou URL.

V případě potřeby můžete [vytvořit vlastní poskytovatele typů](creating-a-type-provider.md)nebo poskytovatele odkazů, které vytvořili jiní uživatelé. Předpokládejme například organizaci, která má datovou službu poskytující velké a zvyšující se množství pojmenovaných datových sad, přičemž každá z nich má vlastní stabilní schéma dat. Můžete vytvořit poskytovatele typů, který schémata přečte a nabídne programátorům nejnovější dostupné datové sady se silnými typy.

## <a name="see-also"></a>Viz také

- [Kurz: vytvoření poskytovatele typu](creating-a-type-provider.md)
- [Referenční dokumentace jazyka F #](../../language-reference/index.md)
