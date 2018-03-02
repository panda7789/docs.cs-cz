---
title: "Zprostředkovatelé typů"
description: "Zjistěte, jak poskytovatele typu F # je komponenta, která poskytuje typy, vlastnosti a metody pro použití ve vašich aplikacích."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 25697ef6-465e-4248-9de5-1d199d4a8b59
ms.openlocfilehash: f721b5b378bf70fb594cad66bd90bd96a0320ee2
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="type-providers"></a>Zprostředkovatelé typů

> [!NOTE]
Tato příručka byla zapsána z F # 3.0 a budou aktualizovány.  V tématu [FSharp.Data](https://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.

Poskytovatel typů jazyka F# je komponenta, která poskytuje typy, vlastnosti a metody pro váš program. Poskytovatelé typů jsou významnou součástí podpory informačně obsáhlého programování v jazyce F# 3.0. Klíčem k informačně obsáhlému programování je odstranění bariér, které překážejí v práci s rozličnými zdroji informací nalezenými na Internetu a v moderních podnikových prostředích. Jednou takovou významnou překážkou pro zahrnutí zdroje informací do programu je nutnost reprezentovat tyto informace jako typy, vlastnosti a metody pro prostředí programovacího jazyka. Ruční psaní těchto typů je časově velmi náročné a obtížné na správu. Běžnou alternativou je použití generátoru kódu, který do projektu přidává soubory. Konvenční typy generování kódu však nelze dobře integrovat do průzkumných režimů programování podporovaných jazykem F#, protože generovaný kód musí být nahrazen vždy, když je upraven odkaz na službu.

Typy poskytované poskytovateli typů jazyka F# jsou obvykle založeny na externích zdrojích informací. Například poskytovatel typů jazyka F# pro SQL poskytne typy, vlastnosti a metody potřebné pro přímou práci s tabulkami libovolné databáze SQL, ke které máte přístup. Obdobným způsobem poskytovatel typů pro webové služby WSDL poskytne typy, vlastnosti a metody potřebné pro přímou práci s libovolnou webovou službou WSDL.

Sada typů, vlastností a metod od poskytovatele typů jazyka F# může záviset na parametrech daných kódem programu. Poskytovatel typů může například poskytnout různé typy v závislosti na připojovacím řetězci nebo adrese URL služby. Tímto způsobem je informační prostor dostupný prostřednictvím připojovacího řetězce nebo adresy URL přímo integrován s programem. Poskytovatel typů dokáže také zajistit, aby skupiny typů byly rozbaleny dle potřeby. To znamená, že jsou rozbalovány, pokud je na typy v programu skutečně odkazováno. To umožňuje přímou integraci rozsáhlých informačních prostorů přístupných na vyžádání, jako jsou například online datové trhy, způsobem využívajícím silné typy.

Jazyk F# obsahuje několik předdefinovaných poskytovatelů typů pro běžně používané internetové a firemní datové služby. Tito poskytovatelé typů přináší jednoduchý a pravidelný přístup k relačním databázím SQL a síťově orientovaným službám OData a WSDL a podporují používání dotazů jazyka F# LINQ na tyto datové zdroje.

V případě potřeby lze vytvořit vlastní poskytovatele typů nebo vytvořit odkaz na poskytovatele typů vytvořené jinými programátory. Předpokládejme například organizaci, která má datovou službu poskytující velké a zvyšující se množství pojmenovaných datových sad, přičemž každá z nich má vlastní stabilní schéma dat. Můžete vytvořit poskytovatele typů, který schémata přečte a nabídne programátorům nejnovější dostupné datové sady se silnými typy.


## <a name="related-topics"></a>Související témata


|Název|Popis|
|-----|-----------|
|[Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů](accessing-a-sql-database.md)|Vysvětluje způsob používání poskytovatele typů SqlDataConnection pro přístup k tabulkám a uloženým procedurám databáze SQL na základě připojovacího řetězce pro přímé připojení k databázi. Přístup využívá mapování technologie LINQ to SQL.|
|[Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů a entit](accessing-a-sql-database-entities.md)|Vysvětluje způsob používání poskytovatele typů SqlEntityConnection pro přístup k tabulkám a uloženým procedurám databáze SQL na základě připojovacího řetězce pro přímé připojení k databázi. Přístup využívá mapování LINQ to Entities. Tato metoda funguje s libovolnou databází, uveden je však příklad systému SQL Server.|
|[Návod: Přístup ke službě OData s použitím zprostředkovatelů typů](accessing-an-odata-service.md)|Vysvětluje způsob používání poskytovatele typů ODataService pro přístup ke službě OData způsobem podporujícím silné typy podle adresy URL služby.|
|[Návod: Přístup k webové službě s použitím zprostředkovatelů typů](accessing-a-web-service.md)|Vysvětluje způsob používání poskytovatele typů WsdlService pro přístup k webové službě WSDL způsobem podporujícím silné typy podle adresy URL služby.|
|[Návod: Generování Př &#35; Typy ze souboru DBML](generating-fsharp-types-from-dbml.md)|Vysvětluje způsob používání poskytovatele typů DmblFile pro přístup k tabulkám a uloženým procedurám databáze SQL na základě souboru DBML, v němž je uložena specifikace schématu databáze technologie LINQ to SQL.|
|[Návod: Generování Př &#35; Typy ze souboru schématu EDMX](generating-fsharp-types-from-edmx.md)|Vysvětluje způsob používání poskytovatele typů EdmxFile pro přístup k tabulkám a uloženým procedurám databáze SQL na základě souboru EDMX, v němž je uložena specifikace schématu Entity Framework.|
|[Kurz: Vytvoření zprostředkovatele typů](creating-a-type-provider.md)|Poskytuje informace o psaní vlastních poskytovatelů typů.|
|[Zabezpečení zprostředkovatele typů](type-provider-security.md)|Poskytuje informace o zásadách bezpečnosti při vývoji poskytovatelů typů.|
|[Řešení potíží se zprostředkovateli typů](troubleshooting-type-providers.md)|Poskytuje informace o běžných problémech, které mohou vzniknout při práci s poskytovateli typů, a zahrnuje návrhy řešení.|

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](../../language-reference/index.md)

[Visual F#](../../index.md)
