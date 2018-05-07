---
title: -main (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 2df02200578979f9a613f43dc92cc9e7b0cb430e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-main-c-compiler-options"></a>-main (možnosti kompilátoru C#)
Tato možnost určuje třídu, která obsahuje položky, přejděte na program, pokud obsahuje více než jedné třídy **hlavní** metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Arguments  
 `class`  
 Typ, který obsahuje **hlavní** metoda.  
  
## <a name="remarks"></a>Poznámky  
 Pokud kompilace obsahuje více než jeden typ s [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metodu, můžete zadat typ, který obsahuje **hlavní** metodu, kterou chcete použít jako vstupní bod do programu.  
  
 Tato možnost je pro použití při kompilaci souboru s příponou .exe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **aplikace** stránku vlastností.  
  
3.  Změnit **spouštěcí objekt** vlastnost.  
  
     Pokud chcete nastavit tuto možnost kompilátoru prostřednictvím kódu programu, najdete v části <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `t2.cs` a `t3.cs`, zadání, **hlavní** metoda najdete ve `Test2`:  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
