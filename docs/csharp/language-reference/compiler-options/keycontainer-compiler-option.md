---
title: -keycontainer (možnosti kompilátoru C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 06a714bf9140ac793e8d853183047ca7255d565e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728985"
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (možnosti kompilátoru C#)
Určuje název kontejneru kryptografických klíčů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 Název kontejner klíče silného názvu.  
  
## <a name="remarks"></a>Poznámky  
 Když **- keycontainer** není použita možnost, kompilátor vytvoří komponentu sdílet. Kompilátor vloží veřejný klíč do manifestu sestavení ze zadaného kontejneru a podepíše konečné sestavení soukromým klíčem. Chcete-li generovat soubor s klíčem, zadejte `sn -k file` na příkazovém řádku. `sn -i` nainstaluje pár klíčů do kontejneru. Tato možnost není podporována při spuštění kompilátoru u CoreCLR. Chcete-li při sestavování u CoreCLR podepsání sestavení, použijte [- keyfile](keyfile-compiler-option.md) možnost.
  
 Pokud kompilujete s [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), název souboru s klíčem je uložené v modulu a součástí sestavení při kompilaci tento modul do sestavení pomocí [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Tuto možnost lze také nastavit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) ve zdrojovém kódu pro jakýkoli modul Microsoft intermediate language (MSIL).  
  
 Můžete také předat údaje o šifrování pro kompilátor [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md). Použití [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Pokud má veřejný klíč do manifestu sestavení, ale chcete zpoždění podepsání sestavení, dokud byl testován.  
  
 Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpožděné podepisování sestavení](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Tato možnost kompilátoru není k dispozici ve vývojovém prostředí sady Visual Studio.  
  
 Programově přístup k této možnosti kompilátoru s <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## <a name="see-also"></a>Viz také:

- [-Keyfile – možnost kompilátoru jazyka C#](keyfile-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
