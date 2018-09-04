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
ms.openlocfilehash: c140a49de0503da1e59396f14ac1aee4c1d7d1a6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511202"
---
# <a name="-lib-c-compiler-options"></a>-lib (možnosti kompilátoru C#)
**-Lib** Určuje umístění sestavení odkazováno prostřednictvím [– referenční dokumentace (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) možnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Arguments  
 `dir1`  
 Adresář pro kompilátor hledat v případě odkazovaných sestavení nebyl nalezen v aktuálním pracovním adresáři (adresář, ze kterého je vyvolán kompilátor) nebo v adresáři systému common language runtime.  
  
 `dir2`  
 Nejmíň jeden další adresáře pro v vyhledat odkazy na sestavení. Další názvy adresářů oddělte čárkou a bez mezer mezi nimi.  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor vyhledá odkazy na sestavení, které nejsou plně kvalifikovaný v následujícím pořadí:  
  
1.  Aktuální pracovní adresář. Toto je adresář, ze kterého je vyvolán kompilátor.  
  
2.  Common language runtime systémový adresář.  
  
3.  Adresáře určeného **-lib**.  
  
4.  Adresáře určené proměnnou prostředí LIB.  
  
 Použití **– referenční dokumentace** zadat odkaz na sestavení.  
  
 **-lib** je sčítání; zadání více než jednou připojí k jakékoli předchozí hodnoty ho.  
  
 O alternativu k použití **-lib** je zkopírovat do pracovního adresáře veškeré požadované sestavení; to vám umožní jednoduše předat název sestavení k **– referenční dokumentace**. Pak můžete odstranit sestavení z pracovního adresáře. Protože není zadána cesta k závislého sestavení v manifestu sestavení, aplikaci lze spustit na cílovém počítači a vyhledá a použití sestavení v globální mezipaměti sestavení.  
  
 Protože kompilátor může odkazovat sestavení, neznamená, že modul common language runtime bude moci najít a načíst sestavení za běhu. Zobrazit [jak modul Runtime vyhledává sestavení](../../../framework/deployment/how-the-runtime-locates-assemblies.md) podrobnosti o tom, jak modul runtime vyhledá odkazovaná sestavení.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno.  
  
2.  Klikněte na tlačítko **cesta k odkazům** stránku vlastností.  
  
3.  Upravte obsah pole se seznamem.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.  
  
## <a name="example"></a>Příklad  
 Zkompilujte t2.cs vytvořte soubor s příponou .exe. Kompilátor bude hledat v pracovním adresáři a v kořenovém adresáři jednotce C odkazy na sestavení.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
