---
title: -delaysign (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: f8525a4e96d172709673b94316b06d815535805f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (možnosti kompilátoru C#)
Tato možnost způsobí, že kompilátor rezervovat místo ve výstupním souboru tak, aby digitální podpis lze přidat později.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-delaysign[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Použití **- delaysign –** Pokud chcete plně podepsané sestavení. Použití **- delaysign +** Pokud chcete umístit veřejný klíč v sestavení. Výchozí hodnota je **- delaysign –**.  
  
## <a name="remarks"></a>Poznámky  
 **- Delaysign** možnost nemá žádný vliv, pokud není použita s [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) nebo [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).  
  
 Pokud budete požadovat plně podepsané sestavení, kompilátor vytvoří hodnotu hash souboru, který obsahuje manifest (metadata sestavení) a podepíše tuto hodnotu hash s privátním klíčem. Výsledný digitální podpis je uložen do souboru obsahujícího manifest. Při sestavení zpoždění, které jsou podepsané, kompilátor nepodporuje výpočetní a uložení podpis, ale rezervy místa v souboru, takže podpis lze přidat později.  
  
 Například pomocí **- delaysign +** umožňuje tester vložení do globální mezipaměti sestavení. Po otestování, je plně podepsat sestavení tak, že privátní klíč sestavení pomocí [Linker sestavení](../../../framework/tools/al-exe-assembly-linker.md) nástroj.  
  
 Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpoždění podepsání sestavení](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete **vlastnosti** stránky pro projekt.  
  
2.  Změnit **zpoždění podepsání** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
