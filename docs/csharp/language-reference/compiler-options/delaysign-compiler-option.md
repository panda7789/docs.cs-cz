---
title: -delaysign (C# možnosti kompilátoru)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: ae309a8de6c4691f0009e5beb8ac2adc8772805b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603024"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (C# možnosti kompilátoru)

Tato možnost způsobí, že kompilátor vyhradí místo ve výstupním souboru, aby bylo možné přidat digitální podpis později.

## <a name="syntax"></a>Syntaxe

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`

Použijte **-delaysign –** Pokud chcete sestavení plně podepsaného. Použijte **-delaysign +** , pokud chcete umístit pouze veřejný klíč do sestavení. Výchozí hodnota je **-delaysign-** .

## <a name="remarks"></a>Poznámky

Možnost **-delaysign** nemá žádný vliv, pokud se nepoužívá s parametrem [-keyfile](./keyfile-compiler-option.md) nebo [-](./keycontainer-compiler-option.md).

Možnosti **-delaysign** a **-publicsign** se vzájemně vylučují.

Když vyžádáte plně podepsané sestavení, kompilátor vyhodnotí hodnotu hash souboru obsahujícího manifest (metadata sestavení) a podepíše tuto hodnotu hash privátním klíčem. Tato operace vytvoří digitální podpis, který je uložený v souboru, který obsahuje manifest. Když je sestavení podepsáno opožděně, kompilátor nevypočítá a uloží podpis, ale rezervuje místo v souboru, aby se podpis mohl přidat později.

Například použití možnosti **-delaysign +** umožní testerovi vložit sestavení do globální mezipaměti. Po otestování můžete sestavení plně podepsat umístěním privátního klíče do sestavení pomocí nástroje [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) .

Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [Zpožděné podepisování sestavení](../../../framework/app-domains/delay-sign-assembly.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete stránku **vlastností** projektu.
1. Upravte vlastnost **pouze** pro Zpožděné podepsání.

Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>v tématu.

## <a name="see-also"></a>Viz také:

- [C#-publicsign – možnost](publicsign-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
