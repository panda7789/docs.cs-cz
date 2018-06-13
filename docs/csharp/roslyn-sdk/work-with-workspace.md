---
title: Práce s modelu SDK pro platformu .NET kompilátoru pracovního prostoru.
description: Tento přehled poskytuje představu o typ, který používáte pro dotazování a zpracování pracovního prostoru a projektů pro váš kód.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 7d450b31cbf2c83c79552d1ace3a1ae692bfdd88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354800"
---
# <a name="work-with-a-workspace"></a>Práce s pracovním prostoru

**Pracovních prostorů** vrstvy je výchozím bodem pro provádění analýzy kódu a refaktoring přes celé řešení. V této vrstvě rozhraní API prostoru vám usnadní uspořádání všechny informace o projekty v řešení do jednoho objektu modelu, nabídky můžete přímý přístup k kompilátoru vrstvy objektové modely jako zdrojový text, syntaxe stromy, sémantických modelů a kompilace bez nutnosti analyzovat souborů, nakonfigurujte možnosti nebo spravovat závislosti mezi projektu. 

Hostitelská prostředí IDE, jako je poskytnout pracovního prostoru vám odpovídající otevřete řešení. Je také možné použít tento model mimo IDE jednoduše načtením soubor řešení.

## <a name="workspace"></a>Pracovní prostor

Pracovní prostor je aktivní reprezentace řešení jako kolekce projektů, každý s kolekci dokumentů. Pracovní prostor je obvykle svázané do prostředí hostitele, který se neustále mění jako typy uživatelů nebo manipuluje s vlastností. 

<xref:Microsoft.CodeAnalysis.Workspace> Poskytuje přístup k aktuální model řešení. Když dojde ke změně v hostitelském prostředí, aktivuje se v pracovním prostoru odpovídající události a <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> vlastnosti. Například když typy uživatelů v textovém editoru odpovídající jedné zdrojové dokumenty, pracovním prostoru používá událost signál, že došlo ke změně celkové model řešení a který dokument byla změněna. Můžete se pak reagovat na tyto změny analýza nový model správnost, zvýraznění oblasti násobek nebo provádění návrhy pro změny kódu. 

Můžete také vytvořit samostatné pracovní prostory, které budou odpojen od hostitelské prostředí nebo používat v aplikaci, která nemá žádné hostitelském prostředí.

## <a name="solutions-projects-documents"></a>Řešení, projekty, dokumenty

I když pracovního prostoru může změnit pokaždé, když stisknutí klávesy, můžete pracovat s modelem řešení v izolaci. 

Řešení je neměnné model projektů a dokumenty. To znamená, že modelu je možné sdílet bez zamknutí nebo duplicita. Po obdržení instance řešení z <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> vlastnost, tato instance bude nikdy nezmění. Však jako s stromy syntaxe a kompilace, můžete upravit řešení vytvořením nové instance na základě existující řešení a konkrétní změny. Potřebujete pracovní prostor, aby se projevily provedené změny, je nutné explicitně použít změněné řešení zpět do pracovního prostoru.

Projekt je součástí modelu celkové neměnné řešení. Reprezentuje všechny dokumenty zdrojového kódu, analýzu a kompilaci možnosti a jak sestavení a odkazy na projekt na projekt. Z projektu dostanete odpovídající kompilace bez nutnosti k určení závislosti projektu nebo analyzovat žádné zdrojové soubory.

Dokument je také součástí modelu celkové neměnné řešení. Dokument představuje jeden zdrojový soubor, ze kterého můžete přístup textového souboru, ke stromu syntaxe a sémantického modelu.

Na následujícím diagramu je reprezentace jak pracovním prostoru souvisí s hostiteli prostředí, nástroje a jak jsou vytvářeny úpravy.

![vztahy mezi různé prvky pracovního prostoru obsahující projekty a zdrojové soubory](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Souhrn

Roslyn zveřejňuje sadu kompilátoru rozhraní API a rozhraní API pracovních prostorů, nabízí bohaté informace o zdrojovém kódu, který má úplný věrnosti s C# a Visual Basic jazyky.  .NET SDK platformy kompilátoru výrazně snižuje překážku vstupu pro vytvoření zaměřené na kód nástrojů a aplikací. Vytvoří mnoho příležitosti pro inovace v oblastech, jako např. meta-programovací generování kódu a transformace, interaktivní použít jazyky C# a VB a vložení jazyka C# a VB v jazycích konkrétní domény.  
