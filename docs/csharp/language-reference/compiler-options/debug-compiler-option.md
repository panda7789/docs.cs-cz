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
ms.openlocfilehash: ab9b299579f9ab4a854ce7ab220edc87e0c66745
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218842"
---
# <a name="-debug-c-compiler-options"></a>-debug (možnosti kompilátoru C#)
**– Ladění** možnost způsobí, že kompilátor generovat ladicí informace a jeho následné uložení do výstupní soubor nebo soubory.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Určení `+`, nebo jenom **– ladění**, způsobí, že kompilátor generovat ladicí informace a umístěte ji do databáze programu (soubor .pdb). Určení `-`, který je v platnosti, pokud nezadáte **– ladění**, způsobí, že žádné informace o ladění, který se má vytvořit.  
  
 `full` &#124; `pdbonly`  
 Určuje typ ladicí informace generované kompilátorem. Úplné argument, který je v platnosti, pokud nezadáte **-debug: pdbonly**, umožňuje připojení k programu spuštěného ladicí program. Zadání pdbonly umožňuje zdrojového kódu, ladění, když program běží v ladicím programu, ale zobrazí jenom assembleru po spuštěným programem k ladicího programu.  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte k vytvoření sestavení pro ladění. Pokud **– ladění**, **– ladění +**, nebo **-debug: full** není zadán, nebudete moci ladit výstupní soubor vašeho programu.  
  
 Pokud používáte **-debug: full**, Upozorňujeme, že se některé vliv na rychlost a velikost za běhu optimalizovaného kódu a malý dopad na kvalitu kódu s **-debug: full**. Doporučujeme, abyste **-debug: pdbonly** nebo žádné PDB pro generování kódu verzi.  
  
> [!NOTE]
>  Jeden rozdíl mezi **-debug: pdbonly** a **– ladění: full** je, že s **– ladění: full** kompilátor vydává <xref:System.Diagnostics.DebuggableAttribute>, sloužící k oznámení kompilátoru JIT zda je k dispozici informace o ladění. Proto obdržíte chybu, pokud váš kód obsahuje <xref:System.Diagnostics.DebuggableAttribute> nastavena na hodnotu false, pokud používáte **-debug: full**.  
  
 Další informace o tom, jak nakonfigurovat ladění výkonu aplikace, najdete v tématu [snadněji bitové kopie pro ladění](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 Chcete-li změnit umístění souboru pdb, [- pdb (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Klikněte **Upřesnit** tlačítko.  
  
4.  Změnit **ladicí informace** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>.  
  
## <a name="example"></a>Příklad  
 Umístí informace o ladění do výstupního souboru `app.pdb`:  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
