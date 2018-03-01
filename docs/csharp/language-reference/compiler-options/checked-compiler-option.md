---
title: "-zaškrtnutí (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c0a8cc66609fe542fc7db166cd208cfcedb204b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-checked-c-compiler-options"></a>-zaškrtnutí (možnosti kompilátoru C#)
**-Zaškrtnutí** možnost určuje, zda celočíselný aritmetický příkaz výsledkem hodnotu, která je mimo rozsah datového typu a zda není v oboru [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) nebo [ nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md) – klíčové slovo, způsobí spuštění výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Poznámky  
 Celočíselný aritmetický příkaz, který je v oboru `checked` nebo `unchecked` – klíčové slovo není v souladu účinku **-zaškrtnutí** možnost.  
  
 Pokud celočíselný aritmetický příkaz, který není v oboru `checked` nebo `unchecked` – klíčové slovo, které jsou výsledkem je hodnota mimo rozsah datového typu, a **-checked +** (**-zaškrtnutí**) se používá v kompilace, že příkaz dojde k výjimce v době běhu. Pokud **- zaškrtnutí -** se používá při kompilaci, že příkaz nezpůsobí výjimku za běhu.  
  
 Výchozí hodnota pro tuto možnost je **- zaškrtnutí -**. Jeden scénář použití **- zaškrtnutí -** je vytváření velkých aplikací. Někdy automatizované nástroje se používají k vytváření těchto aplikací a může takový nástroj automaticky nastaví **-zaškrtnutí** na +. Výchozí globální nástroje můžete přepsat zadáním **- zaškrtnutí -**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky. Další informace najdete v tématu [stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Klikněte **Upřesnit** tlačítko.  
  
4.  Změnit **Kontrola aritmetického přetečení nebo podtečení** vlastnost.  
  
 K této možnosti kompilátoru prostřednictvím kódu programu, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje `t2.cs`. Použití `-checked` v příkazu určuje, že všechny celočíselný aritmetický příkaz v souboru, který není v oboru `checked` nebo `unchecked` – klíčové slovo a jehož výsledkem je hodnota, která je mimo rozsah datového typu, dojde k výjimce při spuštění čas.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
