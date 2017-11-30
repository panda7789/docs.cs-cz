---
title: "-debug (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4705fc6fc3e3fa41f46b8617aa23ab507afa0cd1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="debug-c-compiler-options"></a>/debug (Možnosti kompilátoru C#)
**/Debug** možnost způsobí, že kompilátor generovat ladicí informace a jeho následné uložení do výstupní soubor nebo soubory.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/debug[+ | -]  
/debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Určení `+`, nebo jenom **/debug**, způsobí, že kompilátor generovat ladicí informace a umístěte ji do databáze programu (soubor .pdb). Určení `-`, který je v platnosti, pokud nezadáte **/debug**, způsobí, že žádné informace o ladění, který se má vytvořit.  
  
 `full` &#124; `pdbonly`  
 Určuje typ ladicí informace generované kompilátorem. Úplné argument, který je v platnosti, pokud nezadáte **/debug:pdbonly**, umožňuje připojení k programu spuštěného ladicí program. Zadání pdbonly umožňuje zdrojového kódu, ladění, když program běží v ladicím programu, ale zobrazí jenom assembleru po spuštěným programem k ladicího programu.  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte k vytvoření sestavení pro ladění. Pokud **/debug**, **/debug+**, nebo **/debug:full** není zadán, nebudete moci ladit výstupní soubor vašeho programu.  
  
 Pokud používáte **/debug:full**, uvědomte si, že se některé vliv na rychlost a velikost za běhu optimalizovaného kódu a malý dopad na kvalitu kódu s **/debug:full**. Doporučujeme, abyste **/debug:pdbonly** nebo žádné PDB pro generování kódu verzi.  
  
> [!NOTE]
>  Jeden rozdíl mezi **/debug:pdbonly** a **/debug:full** je, že s **/debug:full** kompilátor vydává <xref:System.Diagnostics.DebuggableAttribute>, který se používá pro oznámení kompilátoru JIT zda je k dispozici informace o ladění. Proto obdržíte chybu, pokud váš kód obsahuje <xref:System.Diagnostics.DebuggableAttribute> nastavena na hodnotu false, pokud používáte **/debug:full**.  
  
 Další informace o tom, jak nakonfigurovat ladění výkonu aplikace, najdete v tématu [snadněji bitové kopie pro ladění](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 Chcete-li změnit umístění souboru pdb, [/pdb (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Klikněte **Upřesnit** tlačítko.  
  
4.  Změnit **ladicí informace** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>.  
  
## <a name="example"></a>Příklad  
 Umístí informace o ladění do výstupního souboru `app.pdb`:  
  
```console  
csc /debug /pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
