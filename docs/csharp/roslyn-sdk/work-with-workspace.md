---
title: Práce s modelem pracovního prostoru .NET Compiler Platform SDK
description: Tento přehled poskytuje porozumění typu, který používáte k dotazování a manipulaci s pracovním prostorem a projekty pro váš kód.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: a2e69129a869707eaec3516310a72f1fc918ca26
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346914"
---
# <a name="work-with-a-workspace"></a>Práce s pracovním prostorem

Vrstva **pracovních prostorů** je výchozím bodem pro provádění analýzy kódu a refaktoringu přes celá řešení. V rámci této vrstvy vám rozhraní API pracovního prostoru pomáhá při organizování všech informací o projektech v řešení do jediného objektového modelu a nabízí vám přímý přístup k modelům objektů vrstvy kompilátoru, jako je zdrojový text, stromy syntaxe, sémantické modely a kompilace bez nutnosti analyzovat soubory, konfigurovat možnosti nebo spravovat závislosti mezi projekty. 

Prostředí hostitele, jako je IDE, poskytují pracovní prostor odpovídající otevřenému řešení. Je také možné použít tento model mimo rozhraní IDE pouhým načtením souboru řešení.

## <a name="workspace"></a>Pracovní prostor

Pracovní prostor je aktivní reprezentace vašeho řešení jako kolekce projektů, z nichž každá má kolekci dokumentů. Pracovní prostor je obvykle svázán s hostitelským prostředím, které se neustále mění jako uživatelské typy nebo pracuje s vlastnostmi. 

<xref:Microsoft.CodeAnalysis.Workspace> poskytuje přístup k aktuálnímu modelu řešení. Když dojde ke změně v hostitelském prostředí, pracovní prostor aktivuje odpovídající události a vlastnost <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> je aktualizována. Například pokud uživatel zadá v textovém editoru odpovídajícím jednomu ze zdrojových dokumentů, použije pracovní prostor událost k signalizaci, že se změnil celkový model řešení a který dokument byl upraven. Pak můžete na tyto změny reagovat tak, že analyzujete nový model tak, aby byly správné, zvýrazňování oblastí významnosti nebo návrh pro změnu kódu. 

Můžete také vytvářet samostatné pracovní prostory, které jsou odpojeny od hostitelského prostředí nebo používány v aplikaci, která nemá žádné hostitelské prostředí.

## <a name="solutions-projects-documents"></a>Řešení, projekty, dokumenty

I když se pracovní prostor může při každém stisknutí klávesy změnit, můžete pracovat s modelem řešení v izolaci. 

Řešení je neměnný model projektů a dokumentů. To znamená, že model lze sdílet bez uzamčení nebo duplikace. Po získání instance řešení z vlastnosti <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> se tato instance nikdy nezmění. Nicméně podobně jako u stromů syntaxe a kompilací můžete upravovat řešení vytvořením nových instancí na základě existujících řešení a konkrétních změn. Chcete-li získat pracovní prostor, aby odrážel vaše změny, je nutné explicitně použít změněné řešení zpátky do pracovního prostoru.

Projekt je součástí celkového modelu neproměnlivého řešení. Představuje všechny dokumenty zdrojového kódu, možnosti analýzy a kompilace a sestavení i odkazy na projekt. Z projektu můžete získat přístup k odpovídající kompilaci bez nutnosti určit závislosti projektu nebo analyzovat všechny zdrojové soubory.

Dokument je také součástí celkového modelu neproměnlivého řešení. Dokument představuje jeden zdrojový soubor, ze kterého můžete získat přístup k textu souboru, stromu syntaxe a sémantickému modelu.

Následující diagram představuje znázornění toho, jak se pracovní prostor týká prostředí hostitele, nástrojů a způsobu provedení úprav.

![vztahy mezi různými prvky pracovního prostoru obsahujícího projekty a zdrojové soubory](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Přehled

Roslyn zpřístupňuje sadu rozhraní API pro kompilátor a pracovní prostory, které poskytují bohatou informaci o zdrojovém kódu a která má plnou věrnost s jazyky C# a Visual Basic.  Sada .NET Compiler Platform SDK výrazně snižuje překážku pro vkládání nástrojů a aplikací zaměřených na kód. Vytváří mnoho příležitostí pro inovace v oblastech, jako jsou meta programování, generování kódu a transformace, interaktivní použití jazyků C# a Visual Basic a vkládání C# a Visual Basic v jazycích specifických pro doménu.  
