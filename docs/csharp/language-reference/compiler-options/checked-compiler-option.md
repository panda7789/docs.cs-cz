---
title: -checked (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: cb4dbadfa4efd0750ffd3dea88a3f661e2f85a8e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173767"
---
# <a name="-checked-c-compiler-options"></a>-checked (C# Možnosti kompilátoru)
Možnost **-checked** určuje, zda celočíselný aritmetický příkaz, jehož výsledkem je hodnota, která je mimo rozsah datového typu a která není v oboru [zaškrtnutého](../keywords/checked.md) nebo [nekontrolovaného](../keywords/unchecked.md) klíčového slova, způsobí výjimku za běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Poznámky  
 Celočíselný aritmetický příkaz, který je `checked` v `unchecked` oboru nebo klíčové slovo, nepodléhá účinku **zaškrtnuté možnosti ..The** integer arithmetic statement that is in the scope of a or keyword is not subject to the effect of the-checked option.  
  
 Pokud celočíselné aritmetické prohlášení, které není `checked` v `unchecked` oboru nebo klíčové slovo má za následek hodnotu mimo rozsah datového typu a **-checked+** (nebo-checked ) se používá v kompilaci, tento příkaz způsobí výjimku v době běhu. **-checked** Pokud **-checked-** se používá v kompilaci, tento příkaz nezpůsobí výjimku za běhu.  
  
 Výchozí hodnota pro tuto možnost je **-checked-**; kontrola přetečení je zakázána.

 Někdy automatizované nástroje, které se používají k vytváření velkých aplikací nastavených na +. Jedním z scénářů pro použití -checked- je přepsat globální výchozí nástroj zadáním -checked-.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu. Další informace naleznete v [tématu Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Klikněte na stránku vlastností **Sestavení.**  
  
3. Klepněte na tlačítko **Upřesnit.**  
  
4. Upravte vlastnost **Kontrola aritmetického přetečení.**  
  
 Chcete-li získat přístup k této <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>možnosti kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje `t2.cs`. Použití `-checked` v příkazu určuje, že všechny celé číslo aritmetické prohlášení v souboru, který není v oboru `checked` nebo `unchecked` klíčové slovo a výsledkem hodnota, která je mimo rozsah datového typu, způsobí výjimku za běhu.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
