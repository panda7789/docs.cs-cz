---
title: -refout (C# možnosti kompilátoru)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 97cbf540527d0449387b71bb1d97df95b6a4aba4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602513"
---
# <a name="-refout-c-compiler-options"></a>-refout (C# možnosti kompilátoru)

Možnost **-refout** Určuje cestu k souboru, kde by měl být výstup referenčního sestavení. To se týká `metadataPeStream` v rozhraní API Emit. Tato možnost odpovídá vlastnosti projektu [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) nástroje MSBuild.

## <a name="syntax"></a>Syntaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath`FilePath pro referenční sestavení. Obecně se musí shodovat s primárním sestavením. Doporučená konvence (používaná nástrojem MSBuild) slouží k umístění referenčního sestavení do podsložky ref/v relativní vzhledem k primárnímu sestavení.

## <a name="remarks"></a>Poznámky

Sestavení pouze s metadaty mají své tělo metody nahrazené jediným `throw null` tělem, ale obsahují všechny členy kromě anonymních typů. Důvodem použití `throw null` těl (na rozdíl od žádného těla) je, že nástroj PEverify může běžet a předávat (čímž ověřuje úplnost metadat).

Referenční sestavení obsahují atribut na úrovni `ReferenceAssembly` sestavení. Tento atribut může být zadán ve zdroji (pak ho kompilátor nebude muset syntetizovat). Z důvodu tohoto atributu modul runtime odmítne načíst referenční sestavení ke spuštění (ale mohou být nadále načtena v režimu pouze pro reflexi). Nástroje, které reflektují sestavení, musí zajistit, aby načetly referenční sestavení pouze v případě reflexe, jinak obdrží chybu výjimek z modulu runtime.

Referenční sestavení dále odstraňují metadata (soukromá členové) od sestavení, která jsou pouze metadata:

- Referenční sestavení obsahuje pouze odkazy na to, co potřebuje na povrchu rozhraní API. Reálné sestavení může mít další odkazy týkající se konkrétních implementací. Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na žádné typy, které jsou požadovány pro. `dynamic`
- Soukromá funkce – členové (metody, vlastnosti a události) jsou odebrány v případech, kdy jejich odebrání nepozorovatelně ovlivní kompilaci. Pokud neexistují žádné <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy, udělejte totéž pro členy vnitřní funkce.
- Všechny typy (včetně privátních nebo vnořených typů) jsou však uloženy v referenčních sestaveních. Všechny atributy jsou zachovány (i interní).
- Všechny virtuální metody jsou zachovány. Explicitní implementace rozhraní jsou zachovány. Explicitně implementované vlastnosti a události jsou zachované, protože jejich přistupující objekty jsou virtuální (a jsou proto zachované).
- Všechna pole struktury jsou zachována. (Toto je kandidát pro upřesnění poC#7,1)

Možnosti `-refout` [a`-refonly`](refonly-compiler-option.md) se vzájemně vylučují.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
