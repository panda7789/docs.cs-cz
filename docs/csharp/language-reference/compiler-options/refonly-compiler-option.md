---
title: -refout (možnosti kompilátoru C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: c15308d27b504f22b266e28f6db0caf837ae36c5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421208"
---
# <a name="-refonly-c-compiler-options"></a>-refout (možnosti kompilátoru C#)

**- Refout** možnost znamená, že referenční sestavení by měl být výstup místo provedení sestavení, jako primární výstup. `-refonly` Parametr tiše zakáže generování souborů pdb, jako referenční sestavení nelze spustit.

## <a name="syntax"></a>Syntaxe

```console
-refonly
```

## <a name="remarks"></a>Poznámky

Obsahující jenom metadata sestavení mají jejich těl metod nahradit pomocí jediného `throw null` textu, ale zahrnout všichni členové s výjimkou anonymních typů. Důvod pro použití `throw null` subjektů (na rozdíl od bez těla) je tak, aby PEVerify může spuštění a předání (tedy ověřování úplnost metadata).

Zahrnout odkaz na sestavení úrovni sestavení `ReferenceAssembly` atribut. Tento atribut může být zadaný ve zdroji (a kompilátor nebude nutné tak, aby odpovídaly ho). Z důvodu tohoto atributu moduly runtime odmítne načíst referenční sestavení pro spuštění (ale stále může být načten v režimu pouze pro reflexi). Nástroje, které odpovídají na sestavení je potřeba zajistit, že se načítají referenční sestavení jako pouze pro reflexi, jinak se mu nepřidají chyby z modulu runtime.

Další referenční sestavení odebrání metadat (soukromé členy) obsahující jenom metadata sestavení:

- Referenční sestavení má jenom odkazy na to, co potřebuje na povrchu API. Skutečné sestavení může mít další odkazy týkající se konkrétní implementace. Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na všechny typy vyžadované pro `dynamic`.
- V případech, kdy jejich odebrání nebude mít vliv na viditelně kompilace se odeberou soukromé funkce členy (metody, vlastnosti a události). Pokud neexistují žádné `InternalsVisibleTo` atributy, provést totéž pro interní členy funkce.
- Ale všechny typy (včetně privátního nebo vnořené typy) jsou uloženy v referenčních sestavení. Všechny atributy jsou udržovány (pravidla i interní).
- Všechny virtuální metody jsou zachovány. Explicitní implementace rozhraní zůstanou. Explicitně implementovaný vlastnosti a události se neodstraní jejich přístupových objektů jsou virtuální (a tedy uchovávají).
- Všechna pole struktury jsou zachovány. (Toto je Release candidate pro metodu post-C# – vylepšení 7.1)

`-refonly` a [ `-refout` ](refout-compiler-option.md) možnosti se vzájemně vylučují.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
