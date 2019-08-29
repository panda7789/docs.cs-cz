---
title: Práce s sémantickým modelem .NET Compiler Platform SDK
description: Tento přehled poskytuje pochopení typu, který používáte pro pochopení a manipulaci s sémantickým modelem kódu.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: c594447bb553f488d60fe83900e2f141608b570f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105671"
---
# <a name="work-with-semantics"></a>Práce se sémantikou

[Stromy syntaxe](work-with-syntax.md) reprezentují lexikální a syntaktickou strukturu zdrojového kódu. I když tyto informace jsou dostatečné pro popis všech deklarací a logiky ve zdroji, není dostatek informací, aby bylo možné zjistit, co je odkazováno. Název může představovat:

- typ
- pole
- Metoda
- lokální proměnná

I když je každá z nich jednoznačně odlišná, určení toho, který identifikátor ve skutečnosti označuje, často vyžaduje důkladné porozumění jazykovým pravidlům. 

Existují prvky programu reprezentované ve zdrojovém kódu a programy mohou také odkazovat na dříve zkompilované knihovny, zabaleny do souborů sestavení. I když žádný zdrojový kód, a proto žádné uzly syntaxe ani stromy nejsou k dispozici pro sestavení, programy mohou stále odkazovat na prvky uvnitř nich.

Pro tyto úlohy potřebujete **sémantický model**.

Kromě syntaktického modelu zdrojového kódu zapouzdřuje sémantický model jazyková pravidla a poskytuje snadný způsob, jak správně porovnat identifikátory se správným prvkem programu, na který se odkazuje.

## <a name="compilation"></a>Kompilace

Kompilace je reprezentace všeho potřebného pro zkompilování C# nebo Visual Basic program, který zahrnuje všechny odkazy na sestavení, možnosti kompilátoru a zdrojové soubory. 

Vzhledem k tomu, že jsou všechny tyto informace na jednom místě, prvky obsažené ve zdrojovém kódu lze podrobněji popsat. Kompilace představuje každý deklarovaný typ, člen nebo proměnnou jako symbol. Kompilace obsahuje nejrůznější metody, které vám pomůžou najít a propojit symboly, které byly buď deklarovány ve zdrojovém kódu nebo importovány jako metadata ze sestavení.

Podobně jako stromy syntaxe jsou kompilace neměnný. Po vytvoření kompilace ji nemůžete změnit vy nebo někdo jiný, se kterou byste ji mohli sdílet. Můžete však vytvořit novou kompilaci z existující kompilace a určit tak jejich změnu. Například můžete vytvořit kompilaci, která je stejná v každém jako existující kompilace, s výjimkou, že může obsahovat další zdrojový soubor nebo odkaz na sestavení.

## <a name="symbols"></a>Symboly

Symbol představuje jedinečný element deklarovaný ve zdrojovém kódu nebo importovaný ze sestavení jako metadata. Každý obor názvů, typ, metoda, vlastnost, pole, událost, parametr nebo místní proměnná jsou reprezentovány symbolem. 

Nejrůznější metody a vlastnosti <xref:Microsoft.CodeAnalysis.Compilation> typu vám pomůžou najít symboly. Například můžete vyhledat symbol deklarovaného typu podle jeho společných metadat. Můžete také přistupovat k celé tabulce symbolů jako strom symbolů, které jsou rootem globálního oboru názvů.

Symboly také obsahují další informace, které kompilátor určí ze zdroje nebo metadat, jako jsou například jiné odkazované symboly. Každý druh symbolu je reprezentován samostatným rozhraním odvozeným od <xref:Microsoft.CodeAnalysis.ISymbol>, z každého s vlastními metodami a vlastnostmi, které podrobně popisují informace, které kompilátor shromáždil. Mnohé z těchto vlastností přímo odkazují na jiné symboly. Například <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> vlastnost oznamuje skutečný symbol typu, na který odkazuje deklarace metody.

Symboly prezentují běžné reprezentace oborů názvů, typů a členů mezi zdrojovým kódem a metadaty. Například metoda, která byla deklarována ve zdrojovém kódu a metoda, která byla importována z metadat, jsou zastoupeny <xref:Microsoft.CodeAnalysis.IMethodSymbol> se stejnou vlastností.

Symboly jsou podobné v konceptu systému typu CLR, jak je reprezentované <xref:System.Reflection> rozhraním API, ale jsou bohatší v tom, že modelují více než jenom typy. Obory názvů, místní proměnné a popisky jsou všechny symboly. Kromě toho symboly jsou reprezentace jazykových konceptů, nikoli konceptů CLR. Existuje velké množství překryvů, ale existuje mnoho smysluplných odlišnosti. Například metoda iterátoru v C# nebo Visual Basic je jedním symbolem. Pokud je však metoda iterátoru přeložena na metadata CLR, jedná se o typ a více metod.

## <a name="semantic-model"></a>Sémantický model

Sémantický model představuje všechny sémantické informace pro jeden zdrojový soubor. Můžete ji použít ke zjištění následujících možností: 

- Symboly odkazované v určitém umístění ve zdroji.
- Výsledný typ libovolného výrazu.
- Všechny diagnostiky, což jsou chyby a upozornění.
- Způsob toku proměnných do oblastí zdroje a mimo ně.
- Odpovědi na více spekulativních otázek.
