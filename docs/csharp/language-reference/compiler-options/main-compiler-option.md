---
title: -Main (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 7d3cfce474023907eda0bc40b692e4bbb65ffb96
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802834"
---
# <a name="-main-c-compiler-options"></a>-Main (možnosti kompilátoru C#)
Tato možnost určuje třídu, která obsahuje vstupní bod pro program, pokud více než jedna třída obsahuje metodu **Main** .  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Arguments  
 `class`  
 Typ, který obsahuje metodu **Main** .  
 Poskytnutý název třídy musí být plně kvalifikovaný; musí zahrnovat úplný obor názvů obsahující třídu následovaný názvem třídy. Například pokud `Main` je metoda umístěna uvnitř `Program` třídy v `MyApplication.Core` oboru názvů, musí být možnost kompilátoru `-main:MyApplication.Core.Program` .
  
## <a name="remarks"></a>Poznámky  
 Pokud vaše kompilace obsahuje více než jeden typ s metodou [Main](../../programming-guide/main-and-command-args/index.md) , můžete určit, který typ obsahuje metodu **Main** , kterou chcete použít jako vstupní bod do programu.  
  
 Tato možnost je určena pro použití při kompilaci souboru. exe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **aplikace** .  
  
3. Upravte vlastnost **objektu po spuštění** .  
  
     Chcete-li nastavit tuto možnost kompilátoru programově, přečtěte si téma <xref:VSLangProj80.ProjectProperties3.StartupObject%2A> .  
  
### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a>Nastavení této možnosti kompilátoru ruční úpravou souboru. csproj
  
Tuto možnost můžete nastavit úpravou souboru. csproj a přidáním prvku `StartupObject` do `PropertyGroup` oddílu. Příklad:

```
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a>Příklad  
 Zkompiluje `t2.cs` a `t3.cs` určí, že metoda **Main** bude nalezena v `Test2` :  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
