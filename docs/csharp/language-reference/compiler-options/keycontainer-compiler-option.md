---
title: -keycontainer (Možnosti kompilátoru Jazyka C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: fead2d4296cfa6fb0195cb4b43f6448c0fc7e6a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970137"
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (Možnosti kompilátoru Jazyka C#)
Určuje název kontejneru kryptografického klíče.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Argumenty  
 `string`  
 Název kontejneru klíče silného názvu.  
  
## <a name="remarks"></a>Poznámky  
 Při použití **-keycontainer** možnost kompilátor vytvoří komponentu sharable. Kompilátor vloží veřejný klíč ze zadaného kontejneru do manifestu sestavení a podepíše konečné sestavení pomocí soukromého klíče. Chcete-li vygenerovat `sn -k file` soubor klíče, zadejte příkaz na příkazovém řádku. `sn -i`nainstaluje dvojici klíčů do kontejneru. Tato možnost není podporována, pokud kompilátor běží na CoreCLR. Chcete-li podepsat sestavení při vytváření na CoreCLR, použijte [-keyfile](keyfile-compiler-option.md) možnost.
  
 Pokud kompilujete s [-target:module](./target-module-compiler-option.md), název souboru klíče je držen v modulu a začleněny do sestavení při kompilaci tohoto modulu do sestavení s [-addmodule](./addmodule-compiler-option.md).  
  
 Tuto možnost můžete také zadat jako<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>vlastní atribut ( ) ve zdrojovém kódu pro libovolný modul zprostředkujícíjazyk společnosti Microsoft (MSIL).  
  
 Můžete také předat informace o šifrování kompilátoru s [-keyfile](./keyfile-compiler-option.md). Použijte [-delaysign,](./delaysign-compiler-option.md) pokud chcete veřejný klíč přidán do manifestu sestavení, ale chcete odložit podepsání sestavení, dokud nebude testováno.  
  
 Další informace naleznete [v tématu Vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Tato možnost kompilátoru není k dispozici ve vývojovém prostředí sady Visual Studio.  
  
 Tuto možnost kompilátoru můžete <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>programově přistupovat pomocí aplikace .  
  
## <a name="see-also"></a>Viz také

- [C# Kompilátor -keyfile, volba](keyfile-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
