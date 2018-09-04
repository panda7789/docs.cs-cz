---
title: -delaysign (možnosti kompilátoru C#)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 105f564d40799c1c006caf8b59d6199dbd8e9318
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518327"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (možnosti kompilátoru C#)

Tato možnost způsobí, že kompilátor rezervuje místo ve výstupním souboru tak, aby digitální podpis se dají přidat později.

## <a name="syntax"></a>Syntaxe

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`

Použití **- delaysign-** potřebujete-li plně podepsané sestavení. Použití **- delaysign +** Pokud chcete umístit veřejný klíč v sestavení. Výchozí hodnota je **- delaysign-**.

## <a name="remarks"></a>Poznámky

**- Delaysign** možnost nemá žádný vliv, pokud nejsou použity s [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) nebo [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).

**- Delaysign** a **- publicsign** možnosti se vzájemně vylučují.

Pokud budete požadovat plně podepsané sestavení, kompilátor vytvoří hodnotu hash souboru, který obsahuje manifest (metadata sestavení) a podepíše tuto hodnotu hash pomocí soukromého klíče. Tato operace vytvoří digitální podpis, který je uložený v souboru, který obsahuje manifest. Pokud je sestavení podepisováno, kompilátor a neukládá podpis, ale rezervuje prostor v souboru tak, že podpis se dají přidat později.

Například použití **- delaysign +** umožňuje testerovi vložit sestavení do globální mezipaměti. Po otestování je tak, že privátní klíč v sestavení s využitím plně podepsat sestavení [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) nástroj.

Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpožděné podepisování sestavení](../../../framework/app-domains/delay-sign-assembly.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřít **vlastnosti** stránky pro projekt.
1. Upravit **zpoždění podepsání** vlastnost.

Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.

## <a name="see-also"></a>Viz také

- [-Publicsign možnosti jazyka C#](publicsign-compiler-option.md)  
- [Možnosti kompilátoru jazyka C#](index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
