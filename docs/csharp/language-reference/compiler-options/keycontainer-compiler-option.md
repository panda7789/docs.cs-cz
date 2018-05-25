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
ms.openlocfilehash: 5a7b378cad7a1df9249fcbefa28bb9aa9a6a3da4
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2018
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (možnosti kompilátoru C#)
Určuje název kontejneru kryptografických klíčů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 Název kontejneru klíčů silným názvem.  
  
## <a name="remarks"></a>Poznámky  
 Když **- keycontainer** možnost, kompilátor vytvoří komponentu lze sdílet. Kompilátor vloží veřejný klíč ze zadaného kontejneru do manifestu a podepíše konečné sestavení s privátním klíčem. Chcete-li vygenerovat soubor klíče, zadejte `sn -k file` na příkazovém řádku. `sn -i` nainstaluje páru klíčů do kontejneru. Tato možnost není podporovaná, když kompilátor běží na CoreCLR. Chcete-li při sestavování na CoreCLR podepsání sestavení, použijte [- keyfile](keyfile-compiler-option.md) možnost.
  
 Pokud je kompilovat s [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), název souboru klíče je udržován v modulu a začleněn do sestavení při kompilaci tohoto modulu do sestavení s [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Tuto možnost můžete také určit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) ve zdrojovém kódu pro libovolný modul (MSIL intermediate language) společnosti Microsoft.  
  
 Vaše informace šifrování můžete předat také kompilátoru s [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md). Použití [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Pokud chcete přidat do manifestu sestavení veřejný klíč, ale chcete zpoždění podepsání sestavení, dokud po testování.  
  
 Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpoždění podepsání sestavení](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Tato možnost kompilátoru není k dispozici ve vývojovém prostředí sady Visual Studio.  
  
 Prostřednictvím kódu programu přístup k této možnosti kompilátoru s <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## <a name="see-also"></a>Viz také  
 [-Keyfile – možnost kompilátor jazyka C#](keyfile-compiler-option.md) [možnosti kompilátoru C#](index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
