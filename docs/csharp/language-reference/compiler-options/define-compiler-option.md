---
title: "-definovat (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 273437a4250a393274fa20ad4c02b61dce35ed34
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-define-c-compiler-options"></a>-definovat (možnosti kompilátoru C#)
**-Definovat** možnost definuje `name` jako symbol v kódu všechny zdrojové soubory vašeho programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Arguments  
 `name`, `name2`  
 Název jeden nebo více znaky, které chcete definovat.  
  
## <a name="remarks"></a>Poznámky  
 **-Definovat** možnost má stejný účinek jako použití [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) direktivy preprocesoru s tím rozdílem, že možnost kompilátoru platí pro všechny soubory v projektu. Symbol zůstává definované ve zdrojovém souboru až [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) – direktiva ve zdrojovém souboru odebere definici. Při použití-define – možnost, `#undef` – direktiva v jednom souboru nemá žádný vliv na jiné soubory zdrojového kódu v projektu.  
  
 Můžete použít symboly, které jsou vytvořené pomocí této možnosti [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) Podmíněná kompilace zdrojové soubory.  
  
 **-d** je zkratka pro **-definovat**.  
  
 Můžete definovat více symbolů s **-definovat** pomocí středníkem nebo čárkou jednotlivé názvy symbolů. Příklad:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 Kompilátor jazyka C#, samotné definuje žádné symboly nebo makra, které můžete použít ve zdrojovém kódu; všechny definice symbolu musí být definovaný uživatelem.  
  
> [!NOTE]
>  C# `#define` neumožňuje symbol má být poskytnut hodnotu jako jazyků, například C++. Například `#define` nelze použít k vytvoření makra nebo definovat konstantu. Pokud potřebujete definovat konstantu, použijte `enum` proměnné. Pokud chcete vytvořit makro ve stylu C++, zvažte možnosti například obecné typy. Vzhledem k tomu, že jsou náchylné makra, C# zakazuje jejich použití, ale poskytuje bezpečnějších alternativ.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Na **sestavení** , zadejte symbol, který má být definován v **Podmíněná kompilace symboly** pole. Například pokud používáte příklad kódu, který následuje, právě zadejte `xx` do textového pole.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
## <a name="example"></a>Příklad  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
