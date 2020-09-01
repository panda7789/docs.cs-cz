---
description: -Checked (možnosti kompilátoru C#)
title: -Checked (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 5c90696edd3031271e16cd2c1a332da5b605f81f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125940"
---
# <a name="-checked-c-compiler-options"></a>-Checked (možnosti kompilátoru C#)
Možnost **-checked** určuje, zda celočíselný aritmetický příkaz, jehož výsledkem je hodnota, která je mimo rozsah datového typu a který není v oboru klíčového slova [checked](../keywords/checked.md) nebo [unchecked](../keywords/unchecked.md) , způsobuje výjimku za běhu.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Poznámky  
 Celočíselný aritmetický příkaz, který je v oboru `checked` `unchecked` klíčového slova or, není v souladu s možností **-checked** .  
  
 Pokud celočíselný aritmetický příkaz, který není v oboru `checked` `unchecked` klíčového slova nebo, má za následek hodnotu mimo rozsah datového typu a **-zaškrtnuto +** (nebo **-checked**), je použita v kompilaci, tento příkaz způsobí výjimku za běhu. Pokud je **zaškrtnuto –** používá se v kompilaci, tento příkaz během běhu nezpůsobí výjimku.  
  
 Výchozí hodnota pro tuto možnost je **-zaškrtnuto –**; kontrola přetečení je zakázána.

 V některých případech se automatizované nástroje, které se používají k sestavení velkých aplikací, zaškrtne na +. Jeden scénář pro použití – zaškrtnuto – slouží k přepsání globální výchozí hodnoty nástroje zadáním-Checked-.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu. Další informace naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Klikněte na tlačítko **Upřesnit** .  
  
4. Upravte vlastnost **check pro aritmetické přetečení** .  
  
 Chcete-li získat přístup k této možnosti kompilátoru programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A> .  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje `t2.cs` . Použití `-checked` v příkazu určuje, že jakýkoli celočíselný aritmetický příkaz v souboru, který není v oboru `checked` `unchecked` klíčového slova or, a který má za následek hodnotu, která je mimo rozsah datového typu, způsobuje výjimku za běhu.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
