---
title: -refout (možnosti kompilátoru C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 34f7b62c0d9a14c52dde0ddd4ac0d5c29a3b5b75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976609"
---
# <a name="-refout-c-compiler-options"></a>-refout (možnosti kompilátoru C#)

**- Refout** možnost určuje, kde referenční sestavení by mělo být výstupní cestu k souboru. To se přeloží na `metadataPeStream` v rozhraní API pro generování. Tato možnost odpovídá nabídce [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) vlastnosti nástroje MSBuild projektu.

## <a name="syntax"></a>Syntaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath` Cesta k souboru pro referenční sestavení. Obecně to by měla odpovídat hodnotě primární sestavení. Doporučené konvence (používány nástrojem MSBuild), je umístit odkaz na sestavení v "ref /" podsložku vzhledem k primární sestavení.

## <a name="remarks"></a>Poznámky

Obsahující jenom metadata sestavení mají jejich těl metod nahradit pomocí jediného `throw null` textu, ale zahrnout všichni členové s výjimkou anonymních typů. Důvod pro použití `throw null` subjektů (na rozdíl od bez těla) je tak, aby PEVerify může spuštění a předání (tedy ověřování úplnost metadata).

Zahrnout odkaz na sestavení úrovni sestavení `ReferenceAssembly` atribut. Tento atribut může být zadaný ve zdroji (a kompilátor nebude nutné tak, aby odpovídaly ho). Z důvodu tohoto atributu moduly runtime odmítne načíst referenční sestavení pro spuštění (ale stále může být načten v režimu pouze pro reflexi). Nástroje, které odpovídají na sestavení je potřeba zajistit, že se načítají referenční sestavení jako pouze pro reflexi, jinak se mu nepřidají chyby z modulu runtime.

Další referenční sestavení odebrání metadat (soukromé členy) obsahující jenom metadata sestavení:

- Referenční sestavení má jenom odkazy na to, co potřebuje na povrchu API. Skutečné sestavení může mít další odkazy týkající se konkrétní implementace. Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na všechny typy vyžadované pro `dynamic`.
- V případech, kdy jejich odebrání nebude mít vliv na viditelně kompilace se odeberou soukromé funkce členy (metody, vlastnosti a události). Pokud neexistují žádné <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy, provést totéž pro interní členy funkce.
- Ale všechny typy (včetně privátního nebo vnořené typy) jsou uloženy v referenčních sestavení. Všechny atributy jsou udržovány (pravidla i interní).
- Všechny virtuální metody jsou zachovány. Explicitní implementace rozhraní zůstanou. Explicitně implementovaný vlastnosti a události se neodstraní jejich přístupových objektů jsou virtuální (a tedy uchovávají).
- Všechna pole struktury jsou zachovány. (Toto je Release candidate pro metodu post-C# – vylepšení 7.1)

`-refout` a [ `-refonly` ](refonly-compiler-option.md) možnosti se vzájemně vylučují.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
