---
description: -Debug (možnosti kompilátoru C#)
title: -Debug (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
ms.openlocfilehash: 164530a5ec99e7d5b9f34dbcdfb18d80f3102308
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125914"
---
# <a name="-debug-c-compiler-options"></a>-Debug (možnosti kompilátoru C#)
Možnost **-Debug** způsobí, že kompilátor vygeneruje ladicí informace a umístí je do výstupního souboru nebo souborů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Zadání `+` nebo pouhého **ladění**způsobí, že kompilátor vygeneruje ladicí informace a umístí je do databáze programu (soubor. pdb). Určení `-` , které platí, pokud nezadáte **-ladit**, nezpůsobí vytvoření žádné ladicí informace.  
  
 `full` &#124; `pdbonly`  
 Určuje typ ladicích informací generovaných kompilátorem. Úplný argument, který je platný, pokud nezadáte **-debug: pdbonly**, umožňuje připojit k běžícímu programu ladicí program. Zadání pdbonly umožňuje ladění zdrojového kódu, když je program spuštěn v ladicím programu, ale zobrazí pouze Assembler, pokud je spuštěný program připojen k ladicímu programu.  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte k vytvoření sestavení ladění. IF **-Debug**, **-Debug +** nebo **-debug: Full** není zadán, nebudete moci ladit výstupní soubor programu.  
  
 Použijete **-li příkaz-Debug: Full**, pamatujte na to, že došlo k nějakému dopadu na rychlost a velikost optimalizovaného kódu JIT a malý dopad na kvalitu kódu pomocí **ladění: Full**. Pro generování kódu vydání doporučujeme **ladit: pdbonly** nebo No PDB.  
  
> [!NOTE]
> Jeden rozdíl mezi **laděním: pdbonly** a **-debug: Full** je to, že with **-debug: Full** vygeneruje kompilátor <xref:System.Diagnostics.DebuggableAttribute> , který slouží k oznámení kompilátoru JIT, že jsou k dispozici informace o ladění. Proto se zobrazí chyba, pokud kód obsahuje hodnotu <xref:System.Diagnostics.DebuggableAttribute> false, pokud použijete **příkaz-Debug: Full**.  
  
 Další informace o tom, jak nakonfigurovat výkon ladění aplikace, najdete v tématu [Vytvoření obrázku pro snadnější ladění](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 Chcete-li změnit umístění souboru PDB, viz [-PDB (možnosti kompilátoru C#)](./pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Klikněte na tlačítko **Upřesnit** .  
  
4. Upravte vlastnost **ladicí informace** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A> .  
  
## <a name="example"></a>Příklad  
 Umístit informace o ladění do výstupního souboru `app.pdb` :  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
