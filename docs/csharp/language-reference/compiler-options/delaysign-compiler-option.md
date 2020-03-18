---
title: -delaysign (C# Možnosti kompilátoru)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 9fdc02c22d9d8c8a709155e43a17ebf0d86dfd69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970446"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (C# Možnosti kompilátoru)

Tato možnost způsobí, že kompilátor rezervovat místo ve výstupním souboru tak, aby digitální podpis lze přidat později.

## <a name="syntax"></a>Syntaxe

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Argumenty

`+`&#124;`-`

Použijte **-delaysign-** pokud chcete plně podepsané sestavení. Použijte **-delaysign+,** pokud chcete umístit veřejný klíč pouze do sestavení. Výchozí hodnota je **-delaysign-**.

## <a name="remarks"></a>Poznámky

Možnost **-delaysign** nemá žádný vliv, pokud není použita s [-keyfile](./keyfile-compiler-option.md) nebo [-keycontainer](./keycontainer-compiler-option.md).

Možnosti **-delaysign** a **-publicsign** se vzájemně vylučují.

Když požadujete plně podepsané sestavení, kompilátor zařazuje soubor, který obsahuje manifest (metadata sestavení) a podepisuje, že hash s privátní klíč. Tato operace vytvoří digitální podpis, který je uložen v souboru, který obsahuje manifest. Při podepsání sestavení kompilátor nevypočítá a uloží podpis, ale rezervuje místo v souboru, takže podpis lze přidat později.

Například pomocí **-delaysign+** umožňuje tester umístit sestavení do globální mezipaměti. Po testování můžete plně podepsat sestavení umístěním soukromého klíče v sestavení pomocí nástroje [Linker sestavení.](../../../framework/tools/al-exe-assembly-linker.md)

Další informace naleznete [v tématu Vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete stránku **Vlastnosti** projektu.
1. Upravte pouze vlastnost **znaménko Zpoždění.**

Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>kompilátoru programově, naleznete v tématu .

## <a name="see-also"></a>Viz také

- [Možnost C# -publicsign](publicsign-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
