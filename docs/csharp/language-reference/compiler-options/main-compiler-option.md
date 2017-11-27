---
title: "-main (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a6dca6e62dbf69783babf2e16dc4e7c36c6705c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="main-c-compiler-options"></a>/main (Možnosti kompilátoru C#)
Tato možnost určuje třídu, která obsahuje položky, přejděte na program, pokud obsahuje více než jedné třídy **hlavní** metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/main:class  
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
csc t2.cs t3.cs /main:Test2  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
