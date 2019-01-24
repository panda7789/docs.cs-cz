---
title: -doc (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: baf0084e6caa3fce8ca8c375bdcc2bcd135fa21e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646799"
---
# <a name="-doc-c-compiler-options"></a>-doc (C# Compiler Options)
**-Doc** možnost umožňuje umístit komentáře dokumentace do souboru XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Výstupní soubor pro XML, který je naplněn komentáře v souborech zdrojového kódu kompilace.  
  
## <a name="remarks"></a>Poznámky  
 V souborech zdrojového kódu je možné zpracovat a přidat do souboru XML dokumentační komentáře, které předcházet následující:  
  
-   Uživatelem definované typy jako [třídy](../../../csharp/language-reference/keywords/class.md), [delegovat](../../../csharp/language-reference/keywords/delegate.md), nebo [rozhraní](../../../csharp/language-reference/keywords/interface.md)  
  
-   Členy jako pole, [události](../../../csharp/language-reference/keywords/event.md), [vlastnost](../../../csharp/programming-guide/classes-and-structs/using-properties.md), nebo – metoda  
  
 Výstup souboru se zdrojovým kódem, který obsahuje hlavní je nejdříve do souboru XML.  
  
 Použít soubor generovaný XML pro použití se službou [IntelliSense](/visualstudio/ide/using-intellisense) funkcí, ponechte název souboru .xml být stejný jako název sestavení, které chcete podporovat a zkontrolujte, že soubor .xml nachází ve stejném adresáři jako sestavení. Proto když sestavení se odkazuje v projektu sady Visual Studio, soubor .xml nenajde také. Zobrazit [zadávání komentářů ke kódu](/visualstudio/ide/supplying-xml-code-comments) a další informace.  
  
 Pokud kompilujete s [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` bude obsahovat \<sestavení > \< /Assembly > značky zadání názvu souboru, který obsahuje manifest sestavení pro výstupní soubor kompilace.  
  
> [!NOTE]
>  -Doc – možnost platí pro všechny vstupní soubory. nebo, pokud v nastavení projektu, všechny soubory v projektu. Chcete-li vypnout upozornění související s komentáře dokumentace pro konkrétní soubor nebo části kódu, použijte [varování #pragma](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Zobrazit [doporučené značky pro dokumentační komentáře](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) způsoby, jak generovat dokumentaci z komentáře v kódu.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **vlastnosti** stránky.  
  
2.  Klikněte na tlačítko **sestavení** kartu.  
  
3.  Upravit **soubor dokumentace XML** vlastnost.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
