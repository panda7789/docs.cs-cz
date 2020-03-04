---
title: -Checked (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 44dc0fc8f50e5248ce2fca17c36f7309a6aca8d1
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239689"
---
# <a name="-checked-c-compiler-options"></a>-Checked (C# možnosti kompilátoru)
Možnost **-checked** určuje, zda celočíselný aritmetický příkaz, jehož výsledkem je hodnota, která je mimo rozsah datového typu a který není v oboru klíčového slova [checked](../keywords/checked.md) nebo [unchecked](../keywords/unchecked.md) , způsobuje výjimku za běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Poznámky  
 Celočíselný aritmetický příkaz, který je v oboru klíčového slova `checked` nebo `unchecked`, nepodléhá vlivu možnosti **-checked** .  
  
 Pokud celočíselný aritmetický příkaz, který není v rozsahu `checked` nebo `unchecked`, má za následek hodnotu mimo rozsah datového typu a **-zaškrtnuto +** (nebo **-checked**) se používá v kompilaci, tento příkaz způsobí výjimku v době běhu. Pokud je **zaškrtnuto –** používá se v kompilaci, tento příkaz během běhu nezpůsobí výjimku.  
  
 Výchozí hodnota pro tuto možnost je **-zaškrtnuto –** ; kontrola přetečení je zakázána.
 
 V některých případech se automatizované nástroje, které se používají k sestavení velkých aplikací, zaškrtne na +. Jeden scénář pro použití – zaškrtnuto – slouží k přepsání globální výchozí hodnoty nástroje zadáním-Checked-.
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu. Další informace naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Klikněte na tlačítko **Upřesnit**.  
  
4. Upravte vlastnost **check pro aritmetické přetečení** .  
  
 Chcete-li získat přístup k této možnosti kompilátoru programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje `t2.cs`. Použití `-checked` v příkazu určuje, že jakýkoli celočíselný aritmetický příkaz v souboru, který není v oboru klíčového slova `checked` nebo `unchecked`, a jehož výsledkem je hodnota, která je mimo rozsah datového typu, způsobuje výjimku za běhu.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
