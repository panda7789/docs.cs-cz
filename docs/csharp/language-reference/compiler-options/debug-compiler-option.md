---
title: -debug (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
ms.openlocfilehash: c0e8909a1e642333e93cfea5dbfde2f6c33c5443
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470954"
---
# <a name="-debug-c-compiler-options"></a>-debug (možnosti kompilátoru C#)
**– Ladění** možnost způsobí, že kompilátor generovat ladicí informace a umístěte ho do výstupního souboru nebo souborů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Určení `+`, nebo jen **– ladění**, způsobí, že kompilátor generovat ladicí informace a umístěte ho do databáze programu (soubor typu .pdb). Určení `-`, který je v platnosti, pokud nezadáte **– ladění**, způsobí, že žádné informace o ladění, který se má vytvořit.  
  
 `full` &#124; `pdbonly`  
 Určuje typ ladicích informací generovaných kompilátorem. Úplné argument, který je v platnosti, pokud nezadáte **-debug: pdbonly**, umožňuje připojení ladicího programu ke spuštěnému programu. Zadání pdbonly umožňuje zdrojového kódu, ladění, když program se spustí v ladicím programu, ale zobrazí jenom assembler když spuštěný program je připojen k ladicímu programu.  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte, chcete-li vytvořit sestavení pro ladění. Pokud **– ladění**, **– ladění +**, nebo **-debug: full** není zadán, nebudete moci ladit výstupní soubor programu.  
  
 Pokud používáte **-debug: full**, mějte na paměti, že se některé vliv na rychlost a velikost optimalizovaný kód JIT a malý vliv na kvalitu kódu s **-debug: full**. Doporučujeme **-debug: pdbonly** nebo žádný soubor PDB pro generování verze kódu.  
  
> [!NOTE]
>  Jedním z rozdílů mezi **-debug: pdbonly** a **-debug: full** je, že u **-debug: full** kompilátor vydá <xref:System.Diagnostics.DebuggableAttribute>, sloužící k kompilátoru JIT že je k dispozici informace o ladění. Proto se zobrazí chyba, pokud váš kód obsahuje <xref:System.Diagnostics.DebuggableAttribute> nastavena na hodnotu false, pokud používáte **-debug: full**.  
  
 Další informace o tom, jak konfigurovat výkon ladění aplikace najdete v tématu [usnadnění bitové kopie k ladění](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 Chcete-li změnit umístění souboru .pdb, [- pdb (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **vlastnosti** stránky.  
  
2.  Klikněte na tlačítko **sestavení** stránku vlastností.  
  
3.  Klikněte na tlačítko **Upřesnit** tlačítko.  
  
4.  Upravit **ladicí informace** vlastnost.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>.  
  
## <a name="example"></a>Příklad  
 Umístit informace o ladění do výstupního souboru `app.pdb`:  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
