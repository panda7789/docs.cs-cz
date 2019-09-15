---
title: -obsahoval (C# možnosti kompilátoru)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: fead2d4296cfa6fb0195cb4b43f6448c0fc7e6a9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970137"
---
# <a name="-keycontainer-c-compiler-options"></a>-obsahoval (C# možnosti kompilátoru)
Určuje název kontejneru kryptografických klíčů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 Název kontejneru klíčů se silným názvem.  
  
## <a name="remarks"></a>Poznámky  
 Je-li použita možnost **-** držitele, kompilátor vytvoří součást, kterou lze sdílet. Kompilátor vloží veřejný klíč ze zadaného kontejneru do manifestu sestavení a podepíše konečné sestavení pomocí privátního klíče. Chcete-li vygenerovat soubor klíče `sn -k file` , zadejte do příkazového řádku. `sn -i`nainstaluje dvojici klíčů do kontejneru. Tato možnost není podporována, pokud kompilátor běží na CoreCLR. Pro podepsání sestavení při sestavování na CoreCLR použijte možnost [-keyfile](keyfile-compiler-option.md) .
  
 Pokud kompilujete pomocí [-target: Module](./target-module-compiler-option.md), název souboru klíče je uložen v modulu a začleněn do sestavení při kompilaci tohoto modulu do sestavení s [-addmodule –](./addmodule-compiler-option.md).  
  
 Tuto možnost lze také zadat jako vlastní atribut (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) ve zdrojovém kódu pro libovolný modul jazyka MSIL (Microsoft Intermediate Language).  
  
 Můžete také předat informace o šifrování kompilátoru s parametrem [-keyfile](./keyfile-compiler-option.md). Použijte [-delaysign](./delaysign-compiler-option.md) , pokud chcete, aby byl do manifestu sestavení přidán veřejný klíč, ale chcete zpozdit podepisování sestavení, dokud nebylo testováno.  
  
 Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [Zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Tato možnost kompilátoru není k dispozici ve vývojovém prostředí sady Visual Studio.  
  
 Pomocí <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>programu můžete programově získat přístup k této možnosti kompilátoru.  
  
## <a name="see-also"></a>Viz také:

- [C#Compiler – možnost kompilátoru](keyfile-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
