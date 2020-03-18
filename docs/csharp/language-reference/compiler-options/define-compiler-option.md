---
title: -define (Možnosti kompilátoru Jazyka C#)
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
ms.openlocfilehash: 4a3622b6acc8ebe9c590b01b67074ae59396fc34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173741"
---
# <a name="-define-c-compiler-options"></a>-define (Možnosti kompilátoru Jazyka C#)
Možnost **-define** definuje `name` jako symbol ve všech souborech zdrojového kódu, které váš program.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `name`, `name2`  
 Název jednoho nebo více symbolů, které chcete definovat.  
  
## <a name="remarks"></a>Poznámky  
 Možnost **-define** má stejný účinek jako použití direktivy preprocesoru [#define](../preprocessor-directives/preprocessor-define.md) s tím rozdílem, že možnost kompilátoru je v platnosti pro všechny soubory v projektu. Symbol zůstane definován ve zdrojovém souboru, dokud [#undef](../preprocessor-directives/preprocessor-undef.md) direktiva ve zdrojovém souboru neodebere definici. Při použití -define možnost, `#undef` směrnice v jednom souboru nemá žádný vliv na jiné soubory zdrojového kódu v projektu.  
  
 Symboly vytvořené touto volbou můžete použít s [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)a [#endif](../preprocessor-directives/preprocessor-endif.md) můžete podmíněně kompilovat zdrojové soubory.  
  
 **-d** je krátká forma **-define**.  
  
 Můžete definovat více symbolů s **-define** pomocí středníku nebo čárky pro oddělení názvů symbolů. Například:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 Samotný kompilátor Jazyka C# nedefinuje žádné symboly nebo makra, které můžete použít ve zdrojovém kódu; všechny definice symbolů musí být definovány uživatelem.  
  
> [!NOTE]
> C# `#define` neumožňuje symbolu, který má být uveden hodnotu, jako v jazycích, jako je například C++. Nelze například `#define` použít k vytvoření makra nebo k definování konstanty. Pokud potřebujete definovat konstantu, `enum` použijte proměnnou. Pokud chcete vytvořit makro stylu C++, zvažte alternativy, jako jsou obecné typy. Vzhledem k tomu, že makra jsou notoricky náchylné k chybám, C# zakazuje jejich použití, ale poskytuje bezpečnější alternativy.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Na kartě **Sestavení** zadejte symbol, který má být definován, do pole **Symboly podmíněné kompilace.** Například pokud používáte příklad kódu, který následuje, stačí zadat `xx` do textového pole.  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>kompilátoru programově, naleznete v tématu .  
  
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

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
