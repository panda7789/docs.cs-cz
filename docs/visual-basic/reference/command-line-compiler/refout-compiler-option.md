---
title: -refout
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 3649a24a52cc6a448ea7cf4d850915adf02147fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348655"
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

The **-refout** option specifies a file path where the reference assembly should be output.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Syntaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

`filepath`  
The path and filename of the reference assembly. It should generally be in a sub-folder of the primary assembly. The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly. All folders in `filepath` must exist; the compiler does not create them.

## <a name="remarks"></a>Poznámky

Visual Basic supports the `-refout` switch starting with version 15.3.

Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface. They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract. For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.

The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.

## <a name="see-also"></a>Viz také:

- [-refonly](refonly-compiler-option.md)
- [Visual Basic Command-Line Compiler](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
