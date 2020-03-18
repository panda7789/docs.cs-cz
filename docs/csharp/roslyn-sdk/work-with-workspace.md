---
title: Práce s modelem pracovního prostoru platformy .NET Compiler Platform SDK
description: Tento přehled poskytuje pochopení typu, který používáte k dotazování a manipulaci s pracovním prostorem a projekty pro váš kód.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: d21873b132d5f0788033693a319e556feeac59a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156880"
---
# <a name="work-with-a-workspace"></a>Práce s pracovním prostorem

Vrstva **pracovních prostorů** je výchozím bodem pro analýzu kódu a refaktoring u celých řešení. V rámci této vrstvy rozhraní WORKSPACE API vám pomůže uspořádat všechny informace o projektech v řešení do jednoho objektového modelu a nabídne přímý přístup k objektovým modelům vrstvy kompilátoru, jako je zdrojový text, stromy syntaxe, sémantické modely a kompilace bez nutnosti analyzovat soubory, konfigurovat možnosti nebo spravovat závislosti mezi projekty.

Hostitelská prostředí, jako je ide, poskytují pracovní prostor pro vás odpovídající otevřené řešení. Je také možné použít tento model mimo ide pouhým načtením souboru řešení.

## <a name="workspace"></a>Pracovní prostor

Pracovní prostor je aktivní reprezentace vašeho řešení jako kolekce projektů, každý se sbírkou dokumentů. Pracovní prostor je obvykle vázán na hostitelské prostředí, které se neustále mění, když uživatel zadá nebo manipuluje s vlastnostmi.

Poskytuje <xref:Microsoft.CodeAnalysis.Workspace> přístup k aktuálnímu modelu řešení. Dojde-li ke změně v hostitelském prostředí, pracovní prostor <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> spustí odpovídající události a vlastnost se aktualizuje. Například když uživatel zadá v textovém editoru odpovídající jeden ze zdrojových dokumentů, pracovní prostor používá událost signál, že celkový model řešení byla změněna a který dokument byl změněn. Na tyto změny pak můžete reagovat analýzou opravy nového modelu, zvýrazněním důležitých oblastí nebo návrhem změny kódu.

Můžete také vytvořit samostatné pracovní prostory, které jsou odpojeny od hostitelského prostředí nebo použity v aplikaci, která nemá žádné hostitelské prostředí.

## <a name="solutions-projects-documents"></a>Řešení, projekty, dokumenty

Přestože se pracovní prostor může změnit při každém stisknutí klávesy, můžete pracovat s modelem řešení izolovaně.

Řešení je neměnný model projektů a dokumentů. To znamená, že model lze sdílet bez uzamčení nebo duplikace. Po získání instance řešení <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> z vlastnosti, tato instance se nikdy nezmění. Stejně jako u syntaktických stromů a kompilací však můžete upravit řešení vytvořením nových instancí založených na existujících řešeních a konkrétních změnách. Chcete-li získat pracovní prostor tak, aby odrážel vaše změny, je nutné explicitně použít změněné řešení zpět do pracovního prostoru.

Projekt je součástí celkového modelu neměnného řešení. Představuje všechny dokumenty zdrojového kódu, možnosti analýzy a kompilace a odkazy na sestavení i projekt na projekt. Z projektu můžete přistupovat k odpovídající kompilaci bez nutnosti určit závislosti projektu nebo analyzovat všechny zdrojové soubory.

Dokument je také součástí celkového modelu neměnného řešení. Dokument představuje jeden zdrojový soubor, ze kterého můžete přistupovat k textu souboru, stromu syntaxe a sémantickému modelu.

Následující diagram představuje, jak pracovní prostor souvisí s hostitelským prostředím, nástroji a jak se provádějí úpravy.

![vztahy mezi různými prvky pracovního prostoru obsahující projekty a zdrojové soubory](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Souhrn

Roslyn zveřejňuje sadu kompilátoru API a pracovníprostory API, která poskytuje bohaté informace o zdrojovém kódu a který má plnou věrnost s jazyky C# a Visual Basic.  Sada SDK platformy kompilátoru .NET výrazně snižuje bariéru vstupu pro vytváření nástrojů a aplikací zaměřených na kód. Vytváří mnoho příležitostí pro inovace v oblastech, jako je metaprogramování, generování kódu a transformace, interaktivní použití jazyka C# a Visual Basic a vkládání jazyka C# a Visual Basic v jazycích specifických pro doménu.  
