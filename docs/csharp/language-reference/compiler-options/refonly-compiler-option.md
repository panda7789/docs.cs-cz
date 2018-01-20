---
title: "-refonly (možnosti kompilátoru C#)"
ms.date: 07/08/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25b0f6e024e194dff641fd5069755d0ea112a50b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-refonly-c-compiler-options"></a>-refonly (možnosti kompilátoru C#)

**- Refonly** možnost označuje, že referenční sestavení by se měly zobrazovat místo implementace sestavení, jako primární výstup. `-refonly` Parametr bezobslužně zakáže výstup vytvořeného soubory PDB, jako referenční sestavení nelze provést.

## <a name="syntax"></a>Syntaxe

```console
-refonly
```

## <a name="remarks"></a>Poznámky

Sestavení obsahující jenom metadata obsahovat jejich základní metoda nahradí jediný `throw null` textu, ale zahrnout všichni členové s výjimkou anonymní typy. Důvod použití `throw null` těla (na rozdíl od žádné těla) je, aby PEVerify může spouštět a předat (tedy ověření úplnost metadat).

Zahrnout odkaz na sestavení úrovni sestavení `ReferenceAssembly` atribut. Tento atribut je možné zadat zdroj (pak kompilátor nebudete muset syntetizace ji). Z důvodu tohoto atributu moduly runtime odmítne načíst odkaz na sestavení pro spuštění (ale stále může být načíst v režimu pouze pro reflexi). Nástroje, které odpovídala v sestavení je potřeba zajistit, aby že jejich načtení referenční sestavení jako pouze pro reflexi, jinak se se zobrazí chyba načtení typu z modulu runtime.

Referenční sestavení další odebrání pouze metadata sestavení metadat (soukromé členy):

- Referenční sestavení má jenom odkazy pro vše potřebné v plochy rozhraní API. Skutečné sestavení může mít další odkazy týkající se konkrétní implementace. Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na žádné typů nezbytných pro `dynamic`.
- V případech, kde jejich odebrání nebude mít vliv na viditelně kompilace se odeberou privátní funkce členy (metody, vlastnosti a události). Pokud neexistují žádné `InternalsVisibleTo` atributy, proveďte pro vnitřní funkce členy stejné.
- Ale všechny typy (včetně privátního nebo vnořené typy) jsou uchovávány v referenční sestavení. Všechny atributy jsou uchovány (i interní ty).
- Všechny virtuální metody jsou zachovány. Explicitní implementace rozhraní jsou zachovány. – Explicitně implementovaná vlastností a událostí jsou zachovány, jako jsou virtuální jejich přístupových objektů (a jsou proto v).
- Všechna pole struktury jsou zachovány. (Toto je kandidátem pro metodu post-C#-7.1 upřesnění)

`-refonly` a [ `-refout` ](refout-compiler-option.md) možnosti se vzájemně vylučují.

## <a name="see-also"></a>Viz také
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
