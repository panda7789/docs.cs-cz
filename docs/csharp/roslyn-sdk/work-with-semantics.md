---
title: "Práce s sémantického modelu SDK pro platformu .NET kompilátoru"
description: "Tento přehled poskytuje představu o typ, který používáte pro pochopení a manipulaci s sémantického modelu kódu."
author: billwagner
ms.author: wiwagn
ms.date: 10/15/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 28366093c516f5367d82c0bdfc53749e764361ef
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2017
---
# <a name="work-with-semantics"></a>Práce s sémantiku

[Syntaxe stromy](work-with-syntax.md) představují lexikální a syntaktická strukturu zdrojového kódu. I když tyto informace samotné dostatek k popisu deklarace a logiku ve zdroji, není dostatek informací k určení, co je odkazováno. Název může představovat:

- Typ
- Pole
- Metoda
- lokální proměnné

I když má každý z těchto jednoznačně jiný, určení, které z nich identifikátor ve skutečnosti odkazuje na často vyžaduje hluboké znalosti jazyka pravidla. 

Program elementy reprezentované ve zdrojovém kódu a programy můžete se také podívat na dříve zkompilované knihovny, zabalené do souborů sestavení. I když žádný zdrojový kód a proto žádné uzly syntaxe nebo stromy, jsou k dispozici pro sestavení, programy mohou stále odkazovat na elementy v nich.

Tyto úlohy, musíte **sémantického modelu**.

Kromě syntaktické model ve zdrojovém kódu zapouzdří sémantického modelu jazyka pravidla, která poskytuje snadný způsob, jak správně odpovídají identifikátory s elementem správný program se na ně odkazovat.

## <a name="compilation"></a>Kompilace

Kompilace je reprezentace vše potřebné pro kompilaci C# nebo Visual Basic program, který zahrnuje všechny odkazy na sestavení, – možnosti kompilátoru a zdrojové soubory. 

Protože tyto informace je na jednom místě, můžete elementů obsažených ve zdrojovém kódu popsané v další podrobnosti. Kompilace představuje každý deklarovaný typ, člen nebo proměnná jako symbol. Kompilace obsahuje celou řadu metod, které vám pomůžou najít a symboly, které deklarován ve zdrojovém kódu nebo importován jako metadat ze sestavení se týkají.

Podobně jako u syntaxe stromy, kompilace se nedá změnit. Po vytvoření kompilace, nelze změnit vy ani nikdo jiný, které může být sdílení se službou. Nové kompilace lze však vytvořit z existující kompilace, zadání změnu jako uděláte. Můžete například vytvořit kompilace, která je stejná každých způsobem jako existující kompilace, s výjimkou může obsahovat odkaz na další zdroje soubor nebo sestavení.

## <a name="symbols"></a>Symboly

Symbol představuje jedinečné element deklarovaná zdrojový kód nebo importovat ze sestavení jako metadata. Každý obor názvů, typ, metoda, vlastnost, pole, události, parametr nebo místní proměnné je reprezentována symbol. 

Různé metody a vlastnosti <xref:Microsoft.CodeAnalysis.Compilation> zadejte vám pomůžou najít symboly. Například můžete vyhledat symbol pro deklarovaný typ jeho běžný název metadat. Můžete také přístup k celé symbol tabulce jako strom symbolů root podle globálního oboru názvů.

Symboly také obsahovat další informace, které určuje kompilátor ze zdroje nebo metadata, například další odkazované symboly. Každý typ symbolu je reprezentována samostatné rozhraní odvozené z <xref:Microsoft.CodeAnalysis.ISymbol>, každou s vlastní metody a vlastnosti s podrobnostmi o informace shromážděné nástrojem kompilátoru. Mnoho z těchto vlastností přímý odkaz jiných symbolů. Například <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> vlastnost řekne, skutečný typ symbol, který odkazuje na deklarace metody.

Symboly k dispozici znázornění běžné obory názvů, typy a členy mezi zdrojový kód a metadata. Například metoda, která byla deklarována ve zdrojovém kódu a metodu, která byla naimportována ze metadata jsou obě reprezentována <xref:Microsoft.CodeAnalysis.IMethodSymbol> za použití stejných vlastností.

Symboly jsou v principu podobná systém typů CLR reprezentovaná <xref:System.Reflection> rozhraní API, ale budou se širší, že se model více než jen typy. Obory názvů, místní proměnné a popisky jsou všechny znaky. Kromě toho jsou symboly reprezentace – jazykové koncepty, není koncepty CLR. Existuje mnoho překrývají, ale existují i mnoho smysluplný rozdíly. Například metodu iterator v C# nebo Visual Basic je jeden symbol. Když metoda iterator převádějí na CLR metadata, je však typu a několik metod.

## <a name="semantic-model"></a>Sémantický model

Sémantický model představuje sémantické informace pro jeden zdrojový soubor. Můžete ho použít ke zjištění těchto: 

* Symboly odkazuje na konkrétní umístění zdroje.
* Výsledný typ jakýkoli výraz.
* Všechny diagnostiky, které jsou chyby a upozornění.
* Jak probíhá proměnné a deaktivovat oblasti zdroje.
* Odpovědi na otázky více spekulativní.
