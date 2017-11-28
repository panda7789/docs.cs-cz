---
title: /netcf
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a75573b0881af71e907a488c2b3c15db3816fc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="netcf"></a>/netcf
Nastaví kompilátor k cíli [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/netcf  
```  
  
## <a name="remarks"></a>Poznámky  
 `/netcf` Možnost příčiny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru k cíli [!INCLUDE[Compact](~/includes/compact-md.md)] místo kompletní [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Funkce jazyka, které je k dispozici pouze v úplném [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] je zakázána.  
  
 `/netcf` Možnost je určena pro použití s [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Jazykové funkce zakázal `/netcf` jsou stejné funkce jazyka, nejsou k dispozici v souborech cílit s `/sdkpath`.  
  
> [!NOTE]
>  `/netcf` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku. `/netcf` Když je možnost nastavena [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] načtení projektu zařízení.  
  
 `/netcf` Možnost změní následující funkce jazyka:  
  
-   [End \<– klíčové slovo > příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md) – klíčové slovo, které ukončí provádění programu, je zakázán. Následující program sestavuje a spouští bez `/netcf` ale selže při kompilaci s `/netcf`.  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   Rozpoznání s pozdní vazby ve všech formulářů, je zakázán. Chyby při kompilaci jsou generovány, pokud došlo k rozpoznaný pozdní vazba scénáře. Následující program sestavuje a spouští bez `/netcf` ale selže při kompilaci s `/netcf`.  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   [Automaticky](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), a [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifikátory jsou zakázány. Syntaxe [deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md) příkaz je také upravit tak, aby `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. Následující kód ukazuje účinku `/netcf` na kompilace.  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   Použití klíčových slov jazyka Visual Basic 6.0, které byly odebrány z [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generuje jiné chybě při `/netcf` se používá. Tato akce ovlivní chybové zprávy pro následující klíčová slova:  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `Myfile.vb` s [!INCLUDE[Compact](~/includes/compact-md.md)], pomocí verze mscorlib.dll a souboru Microsoft.VisualBasic.dll najde v adresáři výchozí instalace z [!INCLUDE[Compact](~/includes/compact-md.md)] na jednotce C. Obvykle byste použili nejnovější verzi [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/ sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
