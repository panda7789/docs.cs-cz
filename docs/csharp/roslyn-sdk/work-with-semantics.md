---
title: Práce s sémantického modelu sada SDK platformy kompilátoru .NET
description: V tomto přehledu znalost typu, který použijete k pochopit a manipulovat s sémantického modelu kódu.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: cf34e2ab9688325f58cb54755db4142a883fca77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706634"
---
# <a name="work-with-semantics"></a>Práce se sémantikou

[Syntaxe stromů](work-with-syntax.md) představují lexikální nebo syntaktické struktury zdrojového kódu. I když tyto informace samotné je dostatečná k popisu deklarace a logiky ve zdroji, není dostatek informací k určení, co je odkazována. Může představovat název:

- Typ
- Pole
- Metoda
- lokální proměnná

I když každá z nich je jednoznačně jiný, určující, která z nich identifikátor ve skutečnosti odkazuje na často vyžaduje hlubší pochopení problematiky jazyka pravidel. 

Existují prvky programu ve zdrojovém kódu a programy lze také odkazovat na dříve zkompilované knihovny, zabalen do souborů sestavení. I když žádný zdrojový kód a proto žádné uzly syntaxe nebo stromové struktury, jsou k dispozici pro sestavení, lze programy stále odkazují na prvky v nich obsažené.

Tyto úlohy, je nutné **sémantického modelu**.

Kromě syntaktické modelu zdrojového kódu zapouzdřuje sémantického modelu jazykových pravidel, poskytuje snadný způsob, jak správně identifikátory dodržovat správný program elementu, na kterou se odkazuje.

## <a name="compilation"></a>Kompilace

Kompilace je reprezentace vše potřebné ke kompilaci C# nebo programu Visual Basic, který obsahuje odkazy na sestavení, možnosti kompilátoru a zdrojové soubory. 

Protože všechny tyto informace jsou na jednom místě, můžete podrobněji popsaný elementů obsažených ve zdrojovém kódu. Kompilace představuje každý deklarovaného typu, člen nebo proměnné jako symbol. Kompilace obsahuje celou řadu metod, které vám pomůžou najít a symboly, které jsou deklarovány ve zdrojovém kódu nebo importovat jako metadat ze sestavení se týkají.

Podobná syntaxe stromů, kompilace jsou neměnné. Po vytvoření kompilaci nelze změnit vy nebo někdo jiný, které mohou být sdílení s. Nové kompilace můžete však vytvořit ze stávající kompilace, zadání změnu, jako je tomu tak. Můžete vytvořit kompilaci, která je stejná každý způsobem jako existující kompilace, s tím rozdílem, může obsahovat odkaz na další zdrojový soubor nebo sestavení.

## <a name="symbols"></a>Symboly

Symbol představuje prvek odlišné deklaroval zdrojový kód nebo importována ze sestavení jako metadata. Každý obor názvů, typ, metoda, vlastnost, pole, události, parametr nebo místní proměnná je reprezentovaný symbolem. 

Různé vlastnosti a metody <xref:Microsoft.CodeAnalysis.Compilation> zadejte vám pomůžou najít symboly. Symbol můžete například vyhledat deklarovaný typ podle běžného názvu metadat. Můžete také přístup k tabulce celý symbol jako strom symboly v globálním oboru názvů root.

Symboly taky obsahovat další informace, které kompilátor určuje ze zdroje nebo metadata, například jiných odkazovaných symbolů. Každý druh symbolu je reprezentována samostatné rozhraní odvozeno od <xref:Microsoft.CodeAnalysis.ISymbol>, každá má svůj vlastní metody a vlastnosti s podrobnostmi o informace shromážděné nástrojem kompilátor. Mnohé z těchto vlastností přímo odkazovat na jiné symboly. Například <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> vlastnost říká, skutečný typ symbolu, který odkazuje deklarace metody.

Symboly k dispozici společné reprezentace obory názvů, typy a členy, mezi zdrojovým kódem a metadata. Například metoda, která byla deklarována ve zdrojovém kódu a metody, které byly naimportovány z metadat obě představují <xref:Microsoft.CodeAnalysis.IMethodSymbol> se stejnými vlastnostmi.

Symboly jsou koncept podobný systém typů CLR reprezentovaná <xref:System.Reflection> rozhraní API, ale že jsou bohatší, v tom, že se model víc než jenom typy. Obory názvů, místní proměnné a popisky jsou všechny symboly. Kromě toho jsou symboly reprezentace – jazykové koncepce, ne CLR koncepty. Dochází k mnoha překrývají, ale existují také mnoho smysluplné rozdíly. Pro instanci metody iterátoru v C# nebo Visual Basic je jeden symbol. Pokud metody iterátoru je přeložen na CLR metadata, je ale typu a několik metod.

## <a name="semantic-model"></a>Sémantický model

Sémantický model představuje sémantické informace pro jeden zdrojový soubor. Slouží ke zjištění následujících akcí: 

* Symboly odkazované v konkrétním umístění ve zdroji.
* Výsledný typ libovolný výraz.
* Všechny diagnostiky, které jsou chyby a upozornění.
* Způsob proměnných se předávají do a z oblasti zdroje.
* Odpovědi na otázky více spekulativního.
