---
title: -defineC# (možnosti kompilátoru)
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
ms.openlocfilehash: d56907493ed24e2ea9fa6568af7441fc81ba1a78
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606959"
---
# <a name="-define-c-compiler-options"></a>-defineC# (možnosti kompilátoru)
Možnost **-define** definuje `name` jako symbol ve všech souborech zdrojového kódu váš program.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Arguments  
 `name`, `name2`  
 Název jednoho nebo více symbolů, které chcete definovat.  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-define** má stejný účinek jako použití direktivy preprocesoru [#define](../preprocessor-directives/preprocessor-define.md) s tím rozdílem, že možnost kompilátoru je platná pro všechny soubory v projektu. Symbol zůstane definován ve zdrojovém souboru, dokud direktiva [#undef](../preprocessor-directives/preprocessor-undef.md) ve zdrojovém souboru definici odstraní. Použijete-li možnost-define, `#undef` direktiva v jednom souboru nemá žádný vliv na jiné soubory zdrojového kódu v projektu.  
  
 Můžete použít symboly vytvořené pomocí této možnosti s [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)a [#endif](../preprocessor-directives/preprocessor-endif.md) ke podmíněnému kompilování zdrojových souborů.  
  
 **-d** je krátká forma **definice**.  
  
 Můžete definovat více symbolů pomocí operátoru **-define** pomocí středníku nebo čárky pro oddělení názvů symbolů. Příklad:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 Samotný C# kompilátor nedefinuje žádné symboly nebo makra, které lze použít ve zdrojovém kódu; všechny definice symbolů musí být definované uživatelem.  
  
> [!NOTE]
>  Nepovoluje, aby se k symbolu dostala hodnota, jako v jazycích, jako je C++například. C# `#define` Například `#define` nelze použít k vytvoření makra nebo k definování konstanty. Pokud potřebujete definovat konstantu, použijte `enum` proměnnou. Chcete-li vytvořit makro C++ stylu, zvažte alternativy jako obecné. Vzhledem k tomu, že makra jsou obvykle odlaďuje náchylná k chybám, neumožňuje jejich použití, C# ale poskytuje bezpečnější alternativy.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Na kartě **sestavení** zadejte symbol, který má být definován v poli **symboly podmíněné kompilace** . Například pokud používáte následující příklad kódu, stačí zadat `xx` do textového pole.  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>v tématu.  
  
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

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
