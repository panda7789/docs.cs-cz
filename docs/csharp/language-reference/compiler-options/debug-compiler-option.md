---
title: -debug (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
ms.openlocfilehash: 8bb2b411dc867b6a43e52058dccf2ac980cf0b1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69922501"
---
# <a name="-debug-c-compiler-options"></a>-debug (Možnosti kompilátoru Jazyka C#)
Možnost **-debug** způsobí, že kompilátor vygeneruje informace o ladění a umístí je do výstupního souboru nebo souborů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Zadání `+`, nebo jen **-debug**, způsobí, že kompilátor generovat informace o ladění a umístit je do databáze programu (.pdb soubor). Zadání `-`, které je v platnosti, pokud nezadáte **-debug**, způsobí, že žádné informace o ladění, které mají být vytvořeny.  
  
 `full`&#124;`pdbonly`  
 Určuje typ informací o ladění generovaných kompilátorem. Úplný argument, který je v platnosti, pokud nezadáte **-debug:pdbonly**, umožňuje připojení ladicího programu ke spuštěnému programu. Zadání pdbonly umožňuje ladění zdrojového kódu při spuštění programu v ladicím programu, ale zobrazí se pouze assembler, pokud je spuštěný program připojen k ladicímu programu.  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte k vytvoření sestavení ladění. Pokud **-debug**, **-debug+** nebo **-debug:full** není zadán, nebude možné ladit výstupní soubor programu.  
  
 Pokud používáte **-debug:full**, uvědomte si, že existuje určitý dopad na rychlost a velikost kódu optimalizovaného pro JIT a malý dopad na kvalitu kódu s **-debug:full**. Doporučujeme **-debug:pdbonly** nebo no PDB pro generování kódu vydání.  
  
> [!NOTE]
> Jeden rozdíl mezi **-debug:pdbonly** a **-debug:full** je, že s **-debug:full** kompilátor vydává <xref:System.Diagnostics.DebuggableAttribute>, který se používá k sdělit kompilátoru JIT, že informace o ladění je k dispozici. Proto se zobrazí chyba, pokud váš <xref:System.Diagnostics.DebuggableAttribute> kód obsahuje sadu na hodnotu false, pokud používáte **-debug:full**.  
  
 Další informace o konfiguraci výkonu ladění aplikace naleznete v tématu [Usnadnění ladění bitové kopie](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 Chcete-li změnit umístění souboru PDB, přečtěte si informace [o tématu -pdb (C# Compiler Options).](./pdb-compiler-option.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Sestavení.**  
  
3. Klepněte na tlačítko **Upřesnit.**  
  
4. Upravte vlastnost **Informace o ladění.**  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Umístění ladicích informací do `app.pdb`výstupního souboru :  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
