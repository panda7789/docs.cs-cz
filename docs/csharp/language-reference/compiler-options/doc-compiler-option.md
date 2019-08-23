---
title: -doc (C# možnosti kompilátoru)
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
ms.openlocfilehash: 21605b30867d7be0b906b431253c183e655bea82
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922485"
---
# <a name="-doc-c-compiler-options"></a>-doc (C# možnosti kompilátoru)
Možnost **-doc** slouží k umístění dokumentačních komentářů do souboru XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Výstupní soubor pro jazyk XML, který je vyplněn komentáři v souborech zdrojového kódu kompilace.  
  
## <a name="remarks"></a>Poznámky  
 V souborech zdrojového kódu lze do souboru XML zpracovat a přidat dokumentační komentáře, které předcházejí následujícímu:  
  
- Takové uživatelsky definované typy jako [Třída](../keywords/class.md), [delegát](../keywords/delegate.md)nebo [rozhraní](../keywords/interface.md)  
  
- Tito členové jako pole, [událost](../keywords/event.md), [vlastnost](../../programming-guide/classes-and-structs/using-properties.md)nebo metoda  
  
 Zdrojový soubor zdrojového kódu, který obsahuje Main, je nejprve výstup do XML.  
  
 Chcete-li použít vygenerovaný soubor. XML pro použití s funkcí [technologie IntelliSense](/visualstudio/ide/using-intellisense) , nechte název souboru. XML stejný jako sestavení, které chcete podporovat, a poté se ujistěte, že soubor. XML je ve stejném adresáři jako sestavení. Proto, pokud je odkazováno na sestavení v projektu sady Visual Studio, je také nalezen soubor. XML. Další informace najdete v tématu [poskytnutí komentářů k kódu](/visualstudio/ide/supplying-xml-code-comments) a další informace.  
  
 Pokud nezkompilujete s [-target: Module](./target-module-compiler-option.md), bude \<obsahovat sestavení\<>/Assembly je > značky, `file` které určují název souboru obsahujícího manifest sestavení pro výstupní soubor kompilace.  
  
> [!NOTE]
> Možnost-doc se vztahuje na všechny vstupní soubory; nebo, pokud je nastavena v nastavení projektu, všechny soubory v projektu. Chcete-li zakázat upozornění související s dokumentačními komentáři pro určitý soubor nebo oddíl kódu, použijte [#pragma upozornění](../preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Způsoby, jak generovat dokumentaci z komentářů v kódu, najdete v tématu [Doporučené značky pro dokumentační komentáře](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na kartu **sestavení** .  
  
3. Upravte vlastnost **souboru dokumentace XML** .  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>v tématu.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
