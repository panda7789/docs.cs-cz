---
title: -lib (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 7db975909f498a0b84e7405a12a8f8ec1e2dd34b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216853"
---
# <a name="-lib-c-compiler-options"></a>-lib (možnosti kompilátoru C#)
**-Lib** možnost určuje umístění sestavení odkazovaných pomocí možnosti [– referenční dokumentace (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) možnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Arguments  
 `dir1`  
 Adresář pro kompilátor hledat v případě odkazované sestavení nebyl nalezen v aktuální pracovní adresář (adresář, ze kterého je vyvolán kompilátor) nebo v adresáři systému modul common language runtime.  
  
 `dir2`  
 Jeden nebo více adresářů pro vyhledávání v odkazy na sestavení. Další adresář názvy oddělte čárkou a bez mezer mezi nimi.  
  
## <a name="remarks"></a>Poznámky  
 Hledání kompilátoru pro odkazy na sestavení, které nejsou plně kvalifikovaný v následujícím pořadí:  
  
1.  Aktuální pracovní adresář. Toto je adresář, ze kterého je vyvolán kompilátor.  
  
2.  Common language runtime systémového adresáře.  
  
3.  Adresáře určené **-lib**.  
  
4.  Adresáře určené proměnná prostředí LIB.  
  
 Použití **– referenční dokumentace** zadat odkaz na sestavení.  
  
 **-lib** je sčítání; zadání je více než jednou připojí k jakékoli předchozí hodnoty.  
  
 Alternativu k použití **-lib** je zkopírovat do pracovního adresáře potřebné sestavení; to vám umožní jednoduše předat název sestavení do **– referenční dokumentace**. Potom můžete odstranit sestavení z pracovní adresář. Vzhledem k tomu, že cesta k závislého sestavení není zadané v manifestu sestavení, aplikaci lze spustit na cílovém počítači a vyhledá a použití sestavení v globální mezipaměti sestavení.  
  
 Protože kompilátor, můžete odkazovat sestavení neznamená, že modul CLR bude moct najít a načíst sestavení za běhu. V tématu [jak modul Runtime vyhledává sestavení](../../../framework/deployment/how-the-runtime-locates-assemblies.md) podrobnosti o vyhledávání odkazovaná sestavení modulu runtime.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno.  
  
2.  Klikněte na tlačítko **odkazy cesta** stránku vlastností.  
  
3.  Upravte obsah pole se seznamem.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.  
  
## <a name="example"></a>Příklad  
 Zkompiluje t2.cs a vytvoří soubor s příponou .exe. Kompilátor bude hledat v pracovní adresář a v kořenovém adresáři jednotky C odkazy na sestavení.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
