---
title: "-keyfile (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fc80c1f6614cdfc8e2f56855d0a0315977316f4c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-keyfile-c-compiler-options"></a>-keyfile (možnosti kompilátoru C#)
Určuje název souboru obsahujícího kryptografický klíč.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|----------|----------------|  
|`file`|Název souboru, který obsahuje složitý název klíče.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud tato možnost se používá, kompilátor vloží veřejný klíč ze zadaného souboru do manifestu a následně podepíše konečné sestavení s privátním klíčem. Chcete-li vygenerovat soubor klíče, zadejte sn -k `file` na příkazovém řádku.  
  
 Pokud je kompilovat s **-target: module**, název souboru klíče je udržován v modulu a součástí sestavení, které se vytvoří při kompilaci sestavení s [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Vaše informace šifrování můžete předat také kompilátoru s [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md). Použití [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Pokud chcete, aby částečně podepsané sestavení.  
  
 V případě, že - keyfile i - keycontainer zadávají ve stejné kompilaci (pomocí parametru příkazového řádku nebo ve vlastních atributů), kompilátor se nejdřív pokusí použít kontejner klíčů. Pokud tato operace úspěšná, je podepsaný sestavení s informacemi v kontejneru klíčů. Pokud kompilátor nenajde kontejner klíčů, zkusí zadaný soubor s - keyfile. Pokud tato operace úspěšná, sestavení je podepsaná pomocí informací v souboru klíče a informace o klíči budou nainstalováni v kontejneru klíčů (podobné sn -i), aby na další kompilace kontejner klíče budou platné.  
  
 Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.  
  
 Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpoždění podepsání sestavení](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete **vlastnosti** stránky pro projekt.  
  
2.  Klikněte **podpisování** stránku vlastností.  
  
3.  Změnit **vyberte soubor klíče se silným názvem** vlastnost.  
  
 Prostřednictvím kódu programu přístup k této možnosti kompilátoru s <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
