---
title: -main (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602734"
---
# <a name="-main-c-compiler-options"></a>-main (Možnosti kompilátoru Jazyka C#)
Tato možnost určuje třídu, která obsahuje vstupní bod do programu, pokud více než jedna třída obsahuje **Main** metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Argumenty  
 `class`  
 Typ, který obsahuje **Main** metoda.  
 Uvedený název třídy musí být plně kvalifikovaný; musí obsahovat celý obor názvů obsahující třídu, následovaný názvem třídy. Například pokud `Main` je metoda umístěna `Program` uvnitř `MyApplication.Core` třídy v oboru názvů, `-main:MyApplication.Core.Program`musí být možnost kompilátoru .
  
## <a name="remarks"></a>Poznámky  
 Pokud kompilace obsahuje více než jeden typ s [Main](../../programming-guide/main-and-command-args/index.md) metoda, můžete určit, který typ obsahuje **Main** metoda, která chcete použít jako vstupní bod do programu.  
  
 Tato možnost je pro použití při kompilaci souboru EXE.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Aplikace.**  
  
3. Upravte vlastnost **Pospuštění objektu.**  
  
     Chcete-li tuto možnost kompilátoru nastavit programově, přečtěte si téma <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
## <a name="example"></a>Příklad  
 Zkompilovat `t2.cs` a `t3.cs`, s uvedením, že **Main** metoda bude nalezena v `Test2`:  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
