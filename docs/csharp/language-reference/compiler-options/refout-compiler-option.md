---
title: -refout (možnosti kompilátoru C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: cb0e26b03841c093f223b3013a0d3c52ffd914c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215274"
---
# <a name="-refout-c-compiler-options"></a>-refout (možnosti kompilátoru C#)

**- Refout** možnost určuje cestu k souboru, kde referenční sestavení by měla být výstup. To znamená, že k `metadataPeStream` v emitování rozhraní API.

## <a name="syntax"></a>Syntaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath` Filepath pro referenční sestavení. Obecně je by měl odpovídat u primárních sestavení. Doporučené konvence (používané MSBuild) je umístit referenční sestavení v "ref nebo" podsložky relativně k primární sestavení.

## <a name="remarks"></a>Poznámky

Sestavení obsahující jenom metadata obsahovat jejich základní metoda nahradí jediný `throw null` textu, ale zahrnout všichni členové s výjimkou anonymní typy. Důvod použití `throw null` těla (na rozdíl od žádné těla) je, aby PEVerify může spouštět a předat (tedy ověření úplnost metadat).

Zahrnout odkaz na sestavení úrovni sestavení `ReferenceAssembly` atribut. Tento atribut je možné zadat zdroj (pak kompilátor nebudete muset syntetizace ji). Z důvodu tohoto atributu moduly runtime odmítne načíst odkaz na sestavení pro spuštění (ale stále může být načíst v režimu pouze pro reflexi). Nástroje, které odpovídala v sestavení je potřeba zajistit, aby že jejich načtení referenční sestavení jako pouze pro reflexi, jinak se se zobrazí chyba načtení typu z modulu runtime.

Referenční sestavení další odebrání pouze metadata sestavení metadat (soukromé členy):

- Referenční sestavení má jenom odkazy pro vše potřebné v plochy rozhraní API. Skutečné sestavení může mít další odkazy týkající se konkrétní implementace. Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na žádné typů nezbytných pro `dynamic`.
- V případech, kde jejich odebrání nebude mít vliv na viditelně kompilace se odeberou privátní funkce členy (metody, vlastnosti a události). Pokud neexistují žádné `InternalsVisibleTo` atributy, proveďte pro vnitřní funkce členy stejné.
- Ale všechny typy (včetně privátního nebo vnořené typy) jsou uchovávány v referenční sestavení. Všechny atributy jsou uchovány (i interní ty).
- Všechny virtuální metody jsou zachovány. Explicitní implementace rozhraní jsou zachovány. – Explicitně implementovaná vlastností a událostí jsou zachovány, jako jsou virtuální jejich přístupových objektů (a jsou proto v).
- Všechna pole struktury jsou zachovány. (Toto je kandidátem pro metodu post-C#-7.1 upřesnění)

`-refout` a [ `-refonly` ](refonly-compiler-option.md) možnosti se vzájemně vylučují.

## <a name="see-also"></a>Viz také
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
