---
description: -define (možnosti kompilátoru C#)
title: -define (možnosti kompilátoru C#)
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
ms.openlocfilehash: 3b7a1c6e92d2c60ce289f29044774c3aa42ca84f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125875"
---
# <a name="-define-c-compiler-options"></a>-define (možnosti kompilátoru C#)
Možnost **-define** definuje `name` jako symbol ve všech souborech zdrojového kódu váš program.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Argumenty  
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
  
 Kompilátor jazyka C# sám nedefinuje žádné symboly nebo makra, které lze použít ve zdrojovém kódu; všechny definice symbolů musí být definované uživatelem.  
  
> [!NOTE]
> Jazyk C# `#define` nepovoluje, aby se symbolu předala hodnota, jako v jazycích, jako je například C++. Například `#define` nelze použít k vytvoření makra nebo k definování konstanty. Pokud potřebujete definovat konstantu, použijte `enum` proměnnou. Chcete-li vytvořit makro stylu C++, zvažte alternativy jako obecné. Vzhledem k tomu, že makra jsou obvykle odlaďuje náchylné k chybám, C# nepovoluje jejich použití, ale poskytuje bezpečnější alternativy.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Na kartě **sestavení** zadejte symbol, který má být definován v poli **symboly podmíněné kompilace** . Například pokud používáte následující příklad kódu, stačí zadat `xx` do textového pole.  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A> .  
  
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

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
