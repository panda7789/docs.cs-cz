---
title: -refout (Možnosti kompilátoru Jazyka C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771763"
---
# <a name="-refout-c-compiler-options"></a>-refout (Možnosti kompilátoru Jazyka C#)

Volba **-refout** určuje cestu k souboru, kde by mělo být výstupní sestavení odkazu. To se `metadataPeStream` promítá do v rozhraní EMIT API. Tato možnost odpovídá vlastnosti [projektu ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) msbuild.

## <a name="syntax"></a>Syntaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Argumenty

 `filepath`Cesta souboru pro referenční sestavení. Obecně by měl odpovídat primární sestavení. Doporučená konvence (používá MSBuild) je umístit referenční sestavení v podsložce "ref/" vzhledem k primární sestavení.

## <a name="remarks"></a>Poznámky

Referenční sestavení jsou zvláštní typ sestavení, které obsahují pouze minimální množství metadat, které jsou nutné k reprezentaci veřejného povrchu rozhraní API knihovny. Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučit všechny implementace členů a deklarace soukromých členů, které nemají žádný pozorovatelný dopad na jejich smlouvy rozhraní API. Další informace naleznete [v tématu Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.

A `-refout` [`-refonly`](refonly-compiler-option.md) možnosti se vzájemně vylučují.

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
