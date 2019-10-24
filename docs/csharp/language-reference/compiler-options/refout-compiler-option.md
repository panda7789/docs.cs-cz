---
title: -refout (C# možnosti kompilátoru)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771763"
---
# <a name="-refout-c-compiler-options"></a>-refout (C# možnosti kompilátoru)

Možnost **-refout** Určuje cestu k souboru, kde by měl být výstup referenčního sestavení. To se týká `metadataPeStream` v rozhraní API pro generování. Tato možnost odpovídá vlastnosti projektu [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) nástroje MSBuild.

## <a name="syntax"></a>Syntaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath` FilePath pro referenční sestavení. Obecně se musí shodovat s primárním sestavením. Doporučená konvence (používaná nástrojem MSBuild) slouží k umístění referenčního sestavení do podsložky ref/v relativní vzhledem k primárnímu sestavení.

## <a name="remarks"></a>Poznámky

Referenční sestavení jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny. Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API. Další informace najdete v tématu [referenční sestavení](../../../standard/assembly/reference-assemblies.md) v příručce .NET.

Možnosti `-refout` a [`-refonly`](refonly-compiler-option.md) se vzájemně vylučují.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
