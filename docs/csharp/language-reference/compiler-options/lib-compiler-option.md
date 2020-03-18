---
title: -lib (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 0c230147be055170ca015f27bd42bb096399405d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606822"
---
# <a name="-lib-c-compiler-options"></a>-lib (Možnosti kompilátoru Jazyka C#)
Možnost **-lib** určuje umístění sestavení odkazovaných pomocí možnosti [-reference (C# Compiler Options).](./reference-compiler-option.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir1`  
 Adresář pro kompilátor, ve kterém se má podívat, pokud odkazované sestavení není nalezeno v aktuálním pracovním adresáři (adresář, ze kterého se odvoláváte na kompilátor) nebo v systémovém adresáři běžného jazyka runtime.  
  
 `dir2`  
 Jeden nebo více dalších adresářů, které mají být vyhledány v odkazech na sestavení. Oddělte další názvy adresářů čárkou a bez mezermezi nimi.  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor hledá odkazy na sestavení, které nejsou plně kvalifikované v následujícím pořadí:  
  
1. Aktuální pracovní adresář. Toto je adresář, ze kterého je vyvolán kompilátor.  
  
2. Systémový adresář běžného běhu runtime.  
  
3. Adresáře určené **parametrem -lib**.  
  
4. Adresáře určené proměnnou prostředí LIB.  
  
 Použijte **-reference** k určení odkazu na sestavení.  
  
 **-lib** je doplňková látka; zadání více než jednou připojí k jakékoli předchozí hodnoty.  
  
 Alternativou k použití **-lib** je zkopírovat do pracovního adresáře všechna požadovaná sestavení; To vám umožní jednoduše předat název sestavení **-reference**. Potom můžete odstranit sestavení z pracovního adresáře. Vzhledem k tomu, že cesta k závislému sestavení není zadána v manifestu sestavení, aplikace může být spuštěna v cílovém počítači a vyhledá a použije sestavení v globální mezipaměti sestavení.  
  
 Vzhledem k tomu, že kompilátor může odkazovat na sestavení neznamená, že běžný jazyk runtime bude moci najít a načíst sestavení za běhu. Podrobnosti o tom, jak runtime vyhledává odkazovaná sestavení, naleznete v tématu [Jak runtime vyhledává sestavení.](../../../framework/deployment/how-the-runtime-locates-assemblies.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete dialogové okno **Stránky vlastností** projektu.  
  
2. Klikněte na stránku **vlastností Cesta odkazů.**  
  
3. Upravte obsah seznamu.  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Zkompilujte t2.cs a vytvořte soubor EXE. Kompilátor bude hledat v pracovním adresáři a v kořenovém adresáři jednotky C pro odkazy na sestavení.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
