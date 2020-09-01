---
description: -refout (možnosti kompilátoru C#)
title: -refout (možnosti kompilátoru C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 424782e4607fea63130e95ab09a671c75fe1404d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128711"
---
# <a name="-refout-c-compiler-options"></a>-refout (možnosti kompilátoru C#)

Možnost **-refout** Určuje cestu k souboru, kde by měl být výstup referenčního sestavení. To se týká `metadataPeStream` v rozhraní API Emit. Tato možnost odpovídá vlastnosti projektu [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) nástroje MSBuild.

## <a name="syntax"></a>Syntaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Argumenty

 `filepath` FilePath pro referenční sestavení. Obecně se musí shodovat s primárním sestavením. Doporučená konvence (používaná nástrojem MSBuild) slouží k umístění referenčního sestavení do podsložky ref/v relativní vzhledem k primárnímu sestavení.

## <a name="remarks"></a>Poznámky

Referenční sestavení jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny. Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API. Další informace najdete v tématu [referenční sestavení](../../../standard/assembly/reference-assemblies.md) v příručce .NET.

`-refout`Možnosti a [`-refonly`](refonly-compiler-option.md) se vzájemně vylučují.

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
