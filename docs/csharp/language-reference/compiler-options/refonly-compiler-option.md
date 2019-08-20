---
title: -Nepoužívejte refout (C# možnosti kompilátoru)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: eb62f98c5d548fe3583d3422eb7b6020a82c296a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606482"
---
# <a name="-refonly-c-compiler-options"></a>-Nepoužívejte refout (C# možnosti kompilátoru)

Možnost **-nepoužívejte refout** označuje, že referenční sestavení by měl být výstupem namísto sestavení implementace jako primární výstup. `-refonly` Parametr tiše zakáže soubory PDB na výstupu, protože referenční sestavení nelze spustit. Tato možnost odpovídá vlastnosti projektu [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) nástroje MSBuild.

## <a name="syntax"></a>Syntaxe

```console
-refonly
```

## <a name="remarks"></a>Poznámky

Sestavení pouze s metadaty mají své tělo metody nahrazené jediným `throw null` tělem, ale obsahují všechny členy kromě anonymních typů. Důvodem použití `throw null` těl (na rozdíl od žádného těla) je, že nástroj PEverify může běžet a předávat (čímž ověřuje úplnost metadat).

Referenční sestavení obsahují atribut na úrovni `ReferenceAssembly` sestavení. Tento atribut může být zadán ve zdroji (pak ho kompilátor nebude muset syntetizovat). Z důvodu tohoto atributu modul runtime odmítne načíst referenční sestavení ke spuštění (ale mohou být nadále načtena v režimu pouze pro reflexi). Nástroje, které reflektují sestavení, musí zajistit, aby načetly referenční sestavení pouze v případě reflexe, jinak obdrží chybu výjimek z modulu runtime.

Referenční sestavení dále odstraňují metadata (soukromá členové) od sestavení, která jsou pouze metadata:

- Referenční sestavení obsahuje pouze odkazy na to, co potřebuje na povrchu rozhraní API. Reálné sestavení může mít další odkazy týkající se konkrétních implementací. Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na žádné typy, které jsou požadovány pro. `dynamic`
- Soukromá funkce – členové (metody, vlastnosti a události) jsou odebrány v případech, kdy jejich odebrání nepozorovatelně ovlivní kompilaci. Pokud neexistují žádné <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributy, udělejte totéž pro členy vnitřní funkce.
- Všechny typy (včetně privátních nebo vnořených typů) jsou však uloženy v referenčních sestaveních. Všechny atributy jsou zachovány (i interní).
- Všechny virtuální metody jsou zachovány. Explicitní implementace rozhraní jsou zachovány. Explicitně implementované vlastnosti a události jsou zachované, protože jejich přistupující objekty jsou virtuální (a jsou proto zachované).
- Všechna pole struktury jsou zachována. (Toto je kandidát pro upřesnění poC#7,1)

Možnosti `-refonly` [a`-refout`](refout-compiler-option.md) se vzájemně vylučují.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
