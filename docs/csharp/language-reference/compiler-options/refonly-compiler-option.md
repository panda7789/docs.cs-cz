---
title: -refonly (Možnosti kompilátoru Jazyka C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72773854"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (Možnosti kompilátoru Jazyka C#)

Možnost **-refonly** označuje, že referenční sestavení by mělo být výstupní místo sestavení implementace jako primární výstup. Parametr `-refonly` tiše zakáže odchozí pdb, jako referenční sestavení nelze provést. Tato možnost odpovídá vlastnosti [projektu ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) msbuild.

## <a name="syntax"></a>Syntaxe

```console
-refonly
```

## <a name="remarks"></a>Poznámky

Referenční sestavení jsou zvláštní typ sestavení, které obsahují pouze minimální množství metadat, které jsou nutné k reprezentaci veřejného povrchu rozhraní API knihovny. Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučit všechny implementace členů a deklarace soukromých členů, které nemají žádný pozorovatelný dopad na jejich smlouvy rozhraní API. Další informace naleznete [v tématu Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.

A `-refonly` [`-refout`](refout-compiler-option.md) možnosti se vzájemně vylučují.

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
