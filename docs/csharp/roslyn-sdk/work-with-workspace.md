---
title: Pracovat s modelu sada SDK platformy kompilátoru .NET pracovního prostoru.
description: V tomto přehledu znalost typu, který používáte k dotazování a manipulaci s pracovních prostorů a projektů pro váš kód.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 7d450b31cbf2c83c79552d1ace3a1ae692bfdd88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706505"
---
# <a name="work-with-a-workspace"></a>Práce s pracovním prostorem

**Pracovní prostory** vrstva je výchozím bodem pro provedení analýzy kódu a refaktoring přes celé řešení. V rámci této vrstvy rozhraní API pro pracovní prostor vám pomůže v uspořádání do jednoho objektu modelu, všechny informace o projekty v řešení nabízející přímý přístup do kompilátoru vrstvy objektové modely jako zdrojový text, stromové struktury syntaxe, sémantickým modelům a kompilace, aniž by bylo nutné analyzovat soubory, konfigurovat možnosti ani spravovat závislostí mezi projekty. 

Hostitelská prostředí, jako je integrované vývojové prostředí, zadejte pracovní prostor můžete otevřít řešení odpovídající. Je také možné použít tento model mimo integrované vývojové prostředí podle jednoduše načítání souboru řešení.

## <a name="workspace"></a>Pracovní prostor

Pracovní prostor je aktivní reprezentace vašeho řešení jako kolekce projektů, každý s kolekcí dokumentů. Pracovní prostor je obvykle vázán na hostitele prostředí, které se neustále mění jako typy uživatelů nebo provádí úpravy vlastnosti. 

<xref:Microsoft.CodeAnalysis.Workspace> Poskytuje přístup k aktuální model řešení. Když dojde ke změně v hostitelském prostředí, aktivuje se v pracovním prostoru odpovídající události a <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> vlastnost aktualizovat. Například když uživatelských typů v textovém editoru odpovídá jedné zdrojové dokumenty, pracovní prostor používá událost na signál, že došlo ke změně celkový model řešení a který dokument byla změněna. Potom můžete reagovat na tyto změny analýza nový model správnost, oblasti významu nebo zajištěním, návrh na změny kódu. 

Můžete také vytvořit samostatný pracovní prostory, které jsou odpojené od hostitelského prostředí nebo použít v aplikaci, která nemá žádné hostitelského prostředí.

## <a name="solutions-projects-documents"></a>Řešení, projekty, dokumenty

I když pracovní prostor může změnit pokaždé, když se stiskne klávesa, můžete pracovat s modelem řešení v izolaci. 

Řešení je neměnný modelu projektů a dokumenty. To znamená, že model lze sdílet bez uzamčení nebo duplicity. Po obdržení instanci řešení z <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> vlastnost, instance se nikdy nezmění. Však stejně jako s stromové struktury syntaxe a kompilace, můžete upravit řešení tak, že vytváří nové instance na základě stávajících řešení a konkrétní změny. Získat pracovní prostor tak, aby odrážely změny, musíte explicitně použít změněné řešení zpět do pracovního prostoru.

Projekt je součástí modelu celkové neměnné řešení. Představuje všechny dokumenty zdrojového kódu, analýzy a kompilace možnosti a jak sestavení a odkazy typu projekt projekt. Z projektu můžete přistupovat odpovídající kompilace, aniž by bylo nutné určit závislosti projektu nebo parsovat žádné zdrojové soubory.

Dokument je také součástí modelu celkové neměnné řešení. Dokument představuje jeden zdrojový soubor, ze kterého přistupujete textového souboru, stromu syntaxe a sémantického modelu.

V následujícím diagramu je reprezentace jak pracovní prostor má vztah k hostiteli prostředí, nástrojů a jak jsou provedeny změny.

![vztahy mezi různé prvky pracovního prostoru obsahující projekty a zdrojové soubory](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Souhrn

Roslyn zveřejňuje sadu kompilátoru rozhraní API a rozhraní API pracovní prostory, které poskytuje podrobné informace o zdrojovém kódu, který má s plnou věrností C# a jazyky Visual Basic.  Sada SDK platformy kompilátoru .NET výrazně snižuje překážku položku pro vytvoření zaměřený na kód nástroje a aplikace. Vytvoří řadu příležitostí pro inovace v oblasti, jako je meta programování, generování kódu a transformace, interaktivní pomocí jazyků C# a VB a vkládání C# a VB v jazycích specifické domény.  
