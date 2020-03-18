---
title: Práce s sémantickým modelem platformy .NET Compiler Platform SDK
description: Tento přehled poskytuje pochopení typu, který používáte k pochopení a manipulaci s sémantickým modelem kódu.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 8575988cd98a4c0ba3f24107788f065f7472f55d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156932"
---
# <a name="work-with-semantics"></a>Práce se sémantikou

[Stromy syntaxe](work-with-syntax.md) představují lexikální a syntaktickou strukturu zdrojového kódu. I když tyto informace samy o sobě stačí k popisu všech deklarací a logiky ve zdroji, není dostatek informací k identifikaci, co je odkazováno. Název může představovat:

- typ
- pole
- Metoda 
- lokální proměnná

I když každý z nich je jedinečně odlišné, určení, který z identifikátorve skutečnosti odkazuje často vyžaduje hluboké pochopení pravidel jazyka.

Ve zdrojovém kódu jsou reprezentovány prvky programu a programy mohou také odkazovat na dříve zkompilované knihovny zabalené v souborech sestavení. Přestože žádný zdrojový kód, a proto žádné syntaktické uzly nebo stromy, jsou k dispozici pro sestavení, programy mohou stále odkazovat na prvky uvnitř nich.

Pro tyto úkoly potřebujete **sémantický model**.

Kromě syntaktického modelu zdrojového kódu sémantický model zapouzdřuje jazyková pravidla, což umožňuje snadný způsob, jak správně spárovat identifikátory se správným programovým prvkem, na který se odkazuje.

## <a name="compilation"></a>Kompilace

Kompilace je reprezentace vše potřebné ke kompilaci c# nebo visual basic program, který obsahuje všechny odkazy sestavení, možnosti kompilátoru a zdrojové soubory.

Vzhledem k tomu, že všechny tyto informace jsou na jednom místě, prvky obsažené ve zdrojovém kódu lze popsat podrobněji. Kompilace představuje každý deklarovaný typ, člen nebo proměnnou jako symbol. Kompilace obsahuje různé metody, které vám pomohou najít a propojit symboly, které byly deklarovány ve zdrojovém kódu nebo importovány jako metadata z sestavení.

Podobně jako syntaxe stromy, kompilace jsou neměnné. Po vytvoření kompilace ji nemůžete změnit vy ani nikdo jiný, s kým ji sdílíte. Můžete však vytvořit novou kompilaci z existující kompilace a určit změnu. Můžete například vytvořit kompilaci, která je ve všech směrech stejná jako existující kompilace, s tím rozdílem, že může obsahovat další zdrojový soubor nebo odkaz na sestavení.

## <a name="symbols"></a>Symboly

Symbol představuje odlišný prvek deklarovaný zdrojovým kódem nebo importovaný ze sestavení jako metadata. Každý obor názvů, typ, metoda, vlastnost, pole, událost, parametr nebo místní proměnná je reprezentován symbolem.

Různé metody a vlastnosti <xref:Microsoft.CodeAnalysis.Compilation> na typu vám pomohou najít symboly. Můžete například najít symbol deklarovaného typu podle jeho společného názvu metadat. Můžete také přistupovat k celé tabulce symbolů jako strom symbolů zakořeněných globálním oborem názvů.

Symboly také obsahují další informace, které kompilátor určuje ze zdroje nebo metadat, jako jsou například jiné odkazované symboly. Každý druh symbolu je reprezentován samostatným rozhraním odvozeným z <xref:Microsoft.CodeAnalysis.ISymbol>, každý s vlastními metodami a vlastnostmi, které podrobně popisují informace, které kompilátor shromáždil. Mnohé z těchto vlastností přímo odkazují na jiné symboly. <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> Vlastnost například sděluje symbol skutečného typu, na který deklarace metody odkazuje.

Symboly představují společnou reprezentaci jmenných prostorů, typů a členů mezi zdrojovým kódem a metadaty. Například metoda, která byla deklarována ve zdrojovém kódu a <xref:Microsoft.CodeAnalysis.IMethodSymbol> metoda, která byla importována z metadat, jsou reprezentovány a se stejnými vlastnostmi.

Symboly jsou podobné v koncepci systému <xref:System.Reflection> typu CLR, jak je reprezentovánrozhraním API, ale jsou bohatší v tom, že modelují více než jen typy. Obory názvů, místní proměnné a popisky jsou všechny symboly. Kromě toho symboly jsou reprezentace konceptů jazyka, nikoli koncepty CLR. Tam je hodně překrývají, ale existuje mnoho smysluplné rozdíly stejně. Například iterátor metoda v jazyce C# nebo Visual Basic je jeden symbol. Však při iterátormetoda je přeložen a CLR metadata, je typ a více metod.

## <a name="semantic-model"></a>Sémantický model

Sémantický model představuje všechny sémantické informace pro jeden zdrojový soubor. Můžete ji použít k zjištění následujících:

- Symboly odkazované na určitém místě ve zdroji.
- Výsledný typ libovolného výrazu.
- Všechny diagnostiky, což jsou chyby a varování.
- Jak proměnné proudí do a z oblastí zdroje.
- Odpovědi na spekulativnější otázky.
