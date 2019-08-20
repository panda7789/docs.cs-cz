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
ms.openlocfilehash: 4e07698e7abdad00983b61412fa2a57e651d4d46
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606996"
---
# <a name="-checked-c-compiler-options"></a>-Checked (C# možnosti kompilátoru)
Možnost **-checked** určuje, zda celočíselný aritmetický příkaz, jehož výsledkem je hodnota, která je mimo rozsah datového typu a který není v oboru klíčového slova [checked](../keywords/checked.md) nebo unchecked [](../keywords/unchecked.md) , způsobuje výjimku za běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Poznámky  
 Celočíselný aritmetický příkaz, který je v oboru `checked` klíčového slova or `unchecked` , není v souladu s možností **-checked** .  
  
 `checked` Pokud celočíselný aritmetický příkaz, který není v oboru klíčového slova nebo `unchecked` , má za následek hodnotu mimo rozsah datového typu a **-zaškrtnuto +** (nebo **-checked**) se používá v kompilaci, tento příkaz způsobí výjimka v době běhu. Pokud je **zaškrtnuto –** používá se v kompilaci, tento příkaz během běhu nezpůsobí výjimku.  
  
 Výchozí hodnota pro tuto možnost je **-zaškrtnuto –** ; kontrola přetečení je zakázána.
 
 V některých případech se automatizované nástroje, které se používají k sestavení velkých aplikací, zaškrtne na +. Jeden scénář pro použití – zaškrtnuto – slouží k přepsání globální výchozí hodnoty nástroje zadáním-Checked-.
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu. Další informace naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Klikněte na tlačítko **Upřesnit** .  
  
4. Upravte vlastnost **check pro vlastnost aritmetického přetečení nebo podtečení** .  
  
 Chcete-li získat přístup k této možnosti <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>kompilátoru programově, přečtěte si téma.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje `t2.cs`. Použití `-checked` v příkazu určuje, že jakýkoli celočíselný aritmetický příkaz v souboru, který není v oboru `checked` klíčového slova or `unchecked` , a který vede k hodnotě, která je mimo rozsah datového typu, způsobuje výjimku při spuštění. interval.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
