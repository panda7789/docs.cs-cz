---
title: -out (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 6c8408c0c613e361dae0c1db19f854e9421ca467
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970383"
---
# <a name="-out-c-compiler-options"></a>-out (Možnosti kompilátoru Jazyka C#)
Volba **-out** určuje název výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Název výstupního souboru vytvořeného kompilátorem.  
  
## <a name="remarks"></a>Poznámky  
 Na příkazovém řádku je možné zadat více výstupních souborů pro kompilaci. Kompilátor očekává, že najít jeden nebo více souborů zdrojového kódu po **-out** možnost. Poté budou všechny soubory zdrojového kódu zkompilovány do výstupního souboru určeného tímto volbou **-out.**  
  
 Zadejte úplný název a příponu souboru, který chcete vytvořit.  
  
 Pokud nezadáte název výstupního souboru:  
  
- A.exe přebere svůj název ze souboru zdrojového kódu, který obsahuje **Metodu Main.**  
  
- Modul .dll nebo .netmodule převezme svůj název z prvního souboru zdrojového kódu.  
  
 Soubor zdrojového kódu použitý ke kompilaci jednoho výstupního souboru nelze použít ve stejné kompilaci pro kompilaci jiného výstupního souboru.  
  
 Při vytváření více výstupních souborů v kompilaci příkazového řádku mějte na paměti, že pouze jeden z výstupních souborů může být sestavení a že pouze první výstupní soubor zadaný (implicitně nebo explicitně s **-out)** může být sestavení.  
  
 Všechny moduly vytvořené jako součást kompilace se stanou soubory přidruženými k libovolnému sestavení, které je také vytvořeno v kompilaci. Pomocí [souboru ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) zobrazíte manifest sestavení a zobrazte přidružené soubory.  
  
 Možnost kompilátoru -out je vyžadována, aby exe bylo cílem sestavení přítele. Další informace naleznete [v tématu Friend Assemblies](../../../standard/assembly/friend.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Aplikace.**  
  
3. Upravte vlastnost **název sestavení.**  
  
     Chcete-li nastavit tuto možnost kompilátoru <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> programově: je vlastnost jen pro čtení, která je určena kombinací typu projektu (exe, knihovna a tak dále) a název sestavení. Změna jedné nebo obou těchto vlastností bude nutné nastavit název výstupního souboru.  
  
## <a name="example"></a>Příklad  
 Kompilovat `t.cs` a `t.exe`vytvářet výstupní `t2.cs` soubor , `mymodule.netmodule`stejně jako vytvořit a vytvořit výstupní soubor modulu :  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Přátelské sestavy](../../../standard/assembly/friend.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
