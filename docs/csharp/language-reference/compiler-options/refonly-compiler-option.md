---
description: -Nepoužívejte refout (možnosti kompilátoru C#)
title: -Nepoužívejte refout (možnosti kompilátoru C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: f9a92462203bedff93a4a711ca8742465b7a561c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124744"
---
# <a name="-refonly-c-compiler-options"></a>-Nepoužívejte refout (možnosti kompilátoru C#)

Možnost **-nepoužívejte refout** označuje, že referenční sestavení by měl být výstupem namísto sestavení implementace jako primární výstup. `-refonly`Parametr tiše zakáže soubory PDB na výstupu, protože referenční sestavení nelze spustit. Tato možnost odpovídá vlastnosti projektu [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) nástroje MSBuild.

## <a name="syntax"></a>Syntax

```console
-refonly
```

## <a name="remarks"></a>Poznámky

Referenční sestavení jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny. Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API. Další informace najdete v tématu [referenční sestavení](../../../standard/assembly/reference-assemblies.md) v příručce .NET.

`-refonly`Možnosti a [`-refout`](refout-compiler-option.md) se vzájemně vylučují.

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
