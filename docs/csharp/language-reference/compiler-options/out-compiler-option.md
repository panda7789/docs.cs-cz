---
description: -out (možnosti kompilátoru C#)
title: -out (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: d1b79879639e1cbdc3dc040977d9fcd0c3a73602
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125017"
---
# <a name="-out-c-compiler-options"></a>-out (možnosti kompilátoru C#)
Možnost **-out** Určuje název výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Název výstupního souboru vytvořeného kompilátorem.  
  
## <a name="remarks"></a>Poznámky  
 Na příkazovém řádku je možné zadat více výstupních souborů pro kompilaci. Kompilátor očekává najít jeden nebo více souborů zdrojového kódu za možností **-out** . Pak všechny soubory se zdrojovým kódem budou zkompilovány do výstupního souboru **určeného parametrem** .  
  
 Zadejte úplný název a příponu souboru, který chcete vytvořit.  
  
 Pokud nezadáte název výstupního souboru:  
  
- Soubor. exe převezme svůj název ze souboru zdrojového kódu, který obsahuje metodu **Main** .  
  
- Soubor. dll nebo. netmodule převezme svůj název z prvního souboru zdrojového kódu.  
  
 Soubor zdrojového kódu, který se používá k kompilování jednoho výstupního souboru, nelze použít ve stejné kompilaci pro kompilaci jiného výstupního souboru.  
  
 Při vytváření více výstupních souborů v kompilaci příkazového řádku mějte na paměti, že pouze jeden z výstupních souborů může být sestavení a že pouze první výstupní soubor (implicitně nebo explicitně s parametrem **-out**) může být sestavení.  
  
 Všechny moduly, které jsou vytvořeny jako součást kompilace, se stanou soubory přidruženými k libovolnému sestavení, které je také vytvořeno v kompilaci. Použijte [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) k zobrazení manifestu sestavení, aby se zobrazily přidružené soubory.  
  
 Možnost kompilátoru-out je povinná, aby byl spustitelný soubor cílem sestavení typu Friend. Další informace naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **aplikace** .  
  
3. Upravte vlastnost **název sestavení** .  
  
     Chcete-li nastavit tuto možnost kompilátoru programově: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> je vlastnost jen pro čtení, která je určena kombinací typu projektu (exe, knihovna a tak dále) a názvu sestavení. Úpravou jedné nebo obou těchto vlastností bude nutné nastavit název výstupního souboru.  
  
## <a name="example"></a>Příklad  
 Zkompilujte `t.cs` a vytvořte výstupní soubor a `t.exe` také vytvořte `t2.cs` a vytvořte výstupní soubor modulu `mymodule.netmodule` :  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Friend – sestavení](../../../standard/assembly/friend.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
