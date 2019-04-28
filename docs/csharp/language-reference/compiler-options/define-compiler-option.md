---
title: -definovat (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 46ceca3a84e8ffbe6d07886c1b93d062f3ccd2d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662956"
---
# <a name="-define-c-compiler-options"></a>-definovat (možnosti kompilátoru C#)
**-Definovat** možnost definuje `name` jako symbol ve zdrojovém kódu všechny soubory programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Arguments  
 `name`, `name2`  
 Název jedné nebo víc symbolů, které chcete definovat.  
  
## <a name="remarks"></a>Poznámky  
 **-Definovat** možnost má stejný účinek jako použití [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) direktivy preprocesoru s tím rozdílem, – možnost kompilátoru platí pro všechny soubory v projektu. Ve zdrojovém souboru, dokud zůstává definovaný symbol [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) směrnice ve zdrojovém souboru odstraní definici. Při použití / define – možnost, `#undef` – direktiva v jednom souboru nemá žádný vliv na jiné soubory zdrojového kódu v projektu.  
  
 Můžete použít symboly vytvořené tímto parametrem [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) Podmíněná kompilace zdrojové soubory.  
  
 **-d** je zkratka pro **-definovat**.  
  
 Můžete definovat více symbolů se **-definovat** pomocí středníkem nebo čárkou, oddělte názvy symbolů. Příklad:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 Samotný kompilátor jazyka C# definuje žádné symboly nebo makra, které můžete použít ve zdrojovém kódu; všechny definice symbolů musí být definovaný uživatelem.  
  
> [!NOTE]
>  C# `#define` neumožňuje symbol, který má být zadána hodnota, stejně jako v jazycích, jako je C++. Například `#define` nelze použít k vytvoření makra nebo chcete-li definovat konstantu. Pokud je potřeba definovat konstantu, použijte `enum` proměnné. Pokud chcete vytvořit makro ve stylu C++, zvažte alternativy, třeba obecných typů. Protože makra jsou náchylné, C# nepovoluje jejich používání, ale poskytuje bezpečnějších alternativ.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete v projektu **vlastnosti** stránky.  
  
2. Na **sestavení** kartu, zadejte symbol, který má být definován v **symboly podmíněné kompilace** pole. Například pokud používáte příklad kódu, který následuje, napsat `xx` do textového pole.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
