---
title: -Main (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602734"
---
# <a name="-main-c-compiler-options"></a>-Main (C# možnosti kompilátoru)
Tato možnost určuje třídu, která obsahuje vstupní bod pro program, pokud více než jedna třída obsahuje metodu **Main** .  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Arguments  
 `class`  
 Typ, který obsahuje metodu **Main** .  
 Poskytnutý název třídy musí být plně kvalifikovaný; musí zahrnovat úplný obor názvů obsahující třídu následovaný názvem třídy. Například pokud `Main` je metoda umístěna `Program` uvnitř třídy v `MyApplication.Core` oboru názvů, musí být `-main:MyApplication.Core.Program`možnost kompilátoru.
  
## <a name="remarks"></a>Poznámky  
 Pokud vaše kompilace obsahuje více než jeden typ s metodou [Main](../../programming-guide/main-and-command-args/index.md) , můžete určit, který typ obsahuje metodu **Main** , kterou chcete použít jako vstupní bod do programu.  
  
 Tato možnost je určena pro použití při kompilaci souboru. exe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **aplikace** .  
  
3. Upravte vlastnost **objektu po spuštění** .  
  
     Chcete-li nastavit tuto možnost kompilátoru programově <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>, přečtěte si téma.  
  
## <a name="example"></a>Příklad  
 Zkompiluje `t2.cs` `Test2`a `t3.cs`určí, že metoda **Main** bude nalezena v:  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
