---
title: -keyfile (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: bd89a5fa58507528b2a70efde04ecd2a6f601b39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605601"
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
|`file`|Název souboru obsahujícího klíč se silným názvem.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud tato možnost se používá, kompilátor vloží veřejný klíč ze zadaného souboru do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem. Chcete-li generovat soubor s klíčem, zadejte sériové číslo -k `file` na příkazovém řádku.  
  
 Pokud kompilujete s **-target: module**, je název souboru klíče uložené v modulu a součástí sestavení, které se vytvoří, když kompilujete sestavení s [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Můžete také předat údaje o šifrování pro kompilátor [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md). Použití [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) potřebujete částečně podepsaného sestavení.  
  
 V případě, že - keyfile a - keycontainer zadávají ve stejné kompilaci (pomocí parametru příkazového řádku nebo pomocí vlastního atributu), kompilátor se nejdřív pokusí použít kontejner klíčů. Pokud tato operace úspěšná, sestavení je podepsáno pomocí informací v kontejneru klíčů. Pokud kompilátor kontejner klíčů nenajde, pokusí se soubor určený parametrem - keyfile. Pokud se tato operace úspěšná, sestavení je podepsáno informacemi ze souboru klíčů a informace o klíči budou nainstalovány do kontejneru klíčů (podobné sn -i) tak, aby při další kompilaci bude platný kontejner klíčů.  
  
 Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.  
  
 Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpožděné podepisování sestavení](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřít **vlastnosti** stránky pro projekt.  
  
2.  Klikněte na tlačítko **podepisování** stránku vlastností.  
  
3.  Upravit **vyberte soubor klíče se silným názvem** vlastnost.  
  
 Programově přístup k této možnosti kompilátoru s <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
