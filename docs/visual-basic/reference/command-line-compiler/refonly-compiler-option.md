---
title: -Nepoužívejte refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 8e64989ac1410b51991027ffcb33e8dae0c0284b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775568"
---
# <a name="-refonly-visual-basic"></a>-Nepoužívejte refout (Visual Basic)

Možnost **-nepoužívejte refout** označuje, že primární výstup kompilace by měl být referenční sestavení namísto sestavení implementace. Parametr `-refonly` tiše zakáže soubory pdbí výstupu, protože referenční sestavení nelze spustit.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Syntaxe

```console
-refonly
```

## <a name="remarks"></a>Poznámky

Visual Basic podporuje přepínač `-refonly` počínaje verzí 15,3.

Referenční sestavení jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny. Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API. Další informace najdete v tématu [referenční sestavení](../../../standard/assembly/reference-assemblies.md) v příručce .NET.

Možnosti `-refonly` a [`-refout`](refout-compiler-option.md) se vzájemně vylučují.

## <a name="see-also"></a>Viz také:

- [-refout](refout-compiler-option.md)
- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
