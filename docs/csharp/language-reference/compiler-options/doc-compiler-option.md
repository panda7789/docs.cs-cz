---
title: "-doc (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c668c79ca2c68d1a497521581857085e57c71f5c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-doc-c-compiler-options"></a>-doc (možnosti kompilátoru C#)
**-Doc** možnost vám umožňuje umístit dokumentační komentáře v souboru XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Výstupní soubor pro formát XML, který je naplněn komentáře ve zdrojových souborech kód kompilace.  
  
## <a name="remarks"></a>Poznámky  
 V soubory zdrojového kódu můžete zpracovat a přidat do souboru XML dokumentační komentáře, které předcházejí následující:  
  
-   Uživatelem definované typy jako [třída](../../../csharp/language-reference/keywords/class.md), [delegovat](../../../csharp/language-reference/keywords/delegate.md), nebo [rozhraní](../../../csharp/language-reference/keywords/interface.md)  
  
-   Členy jako pole, [událostí](../../../csharp/language-reference/keywords/event.md), [vlastnost](../../../csharp/programming-guide/classes-and-structs/using-properties.md), nebo – metoda  
  
 Výstup souboru zdrojového kódu, který obsahuje hlavní nejprve je do souboru XML.  
  
 Chcete použít soubor .xml vygenerovaný pro použití s [IntelliSense](/visualstudio/ide/using-intellisense) funkci, ponechte název souboru .xml být stejný jako název sestavení, které chcete podporovat a zkontrolujte soubor .xml nachází ve stejném adresáři jako sestavení. Proto při odkazování na sestavení v sadě Visual Studio projektu, soubor .xml nalezen také. V tématu [podporované komentáře kódu](/visualstudio/ide/supplying-xml-code-comments) a další informace.  
  
 Pokud je kompilovat s [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` bude obsahovat \<sestavení >\</assembly > značky zadáním názvu souboru, který obsahuje manifest sestavení pro výstupní soubor kompilace.  
  
> [!NOTE]
>  -Doc možnost se vztahuje na všechny vstupní soubory; nebo, pokud v nastavení projektu, všechny soubory v projektu. Chcete-li zakázat upozornění související s dokumentační komentáře pro konkrétní soubor nebo části kódu, použijte [#pragma – upozornění](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).  
  
 V tématu [doporučené značky pro dokumentační komentáře](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) pro způsoby, jak generovat dokumentaci z komentářů v kódu.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **sestavení** kartě.  
  
3.  Změnit **souborů dokumentace XML** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
