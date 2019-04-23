---
title: -checked (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 814e8f3aa7130c6a64e7e27951854bed7b7cbe6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333935"
---
# <a name="-checked-c-compiler-options"></a>-checked (možnosti kompilátoru C#)
**– Zaškrtnutí** možnost určuje, zda příkaz aritmetické celé číslo, jehož výsledkem hodnotu, která je mimo rozsah datového typu a, který není v oboru [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) nebo [ unchecked](../../../csharp/language-reference/keywords/unchecked.md) – klíčové slovo, způsobí, že výjimka za běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Poznámky  
 Celočíselný aritmetické příkaz, který je v oboru `checked` nebo `unchecked` – klíčové slovo není v souladu s vliv **– zaškrtnutí** možnost.  
  
 Pokud celočíselný aritmetické příkaz, který není v oboru `checked` nebo `unchecked` – klíčové slovo výsledkem je hodnota mimo rozsah datového typu, a **-checked +** (nebo **– zaškrtnutí**) se používá v kompilace, že příkaz dojde k výjimce za běhu. Pokud **- checked –** se používá při kompilaci, že příkaz nezpůsobí výjimku za běhu.  
  
 Výchozí hodnota pro tuto možnost je **- checked –**; je zakázaná kontrola přetečení.
 
 V některých případech automatizované nástroje, které se používají k vytvoření velké aplikace nastavené – kontrola +. Jeden scénář pro používání - checked – je globální výchozí nastavení nástroje přepsat zadáním - checked –.
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete v projektu **vlastnosti** stránky. Další informace najdete v tématu [stránku sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Klikněte na tlačítko **sestavení** stránku vlastností.  
  
3. Klikněte na tlačítko **Upřesnit** tlačítko.  
  
4. Upravit **kontrolovat aritmetické přetečení a podtečení** vlastnost.  
  
 Programový přístup k této možnosti kompilátoru, najdete v článku <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz kompiluje `t2.cs`. Použití `-checked` v příkazu určuje, že všechny aritmetické příkaz celé číslo v souboru, který není v oboru `checked` nebo `unchecked` – klíčové slovo a jehož výsledkem je hodnota, která je mimo rozsah datového typu, dojde k výjimce za běhu čas.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
