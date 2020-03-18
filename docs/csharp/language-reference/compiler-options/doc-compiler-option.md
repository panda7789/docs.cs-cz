---
title: -doc (Možnosti kompilátoru Jazyka C#)
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
ms.openlocfilehash: 01ea71f3de9e30abe25184e38a59f3707b54bd5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73422976"
---
# <a name="-doc-c-compiler-options"></a>-doc (Možnosti kompilátoru Jazyka C#)
Možnost **-doc** umožňuje umístit komentáře dokumentace do souboru XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Výstupní soubor pro XML, který je naplněn komentáři v souborech zdrojového kódu kompilace.  
  
## <a name="remarks"></a>Poznámky  
 V souborech zdrojového kódu mohou být komentáře dokumentace, které předcházejí následujícím uvažování, zpracovány a přidány do souboru XML:  
  
- Takové uživatelem definované typy jako [třída](../keywords/class.md), [delegát](../builtin-types/reference-types.md#the-delegate-type)nebo [rozhraní](../keywords/interface.md)  
  
- Takové členy jako pole, [událost](../keywords/event.md), [vlastnost](../../programming-guide/classes-and-structs/using-properties.md)nebo metoda  
  
 Soubor zdrojového kódu, který obsahuje Main je výstup první do XML.  
  
 Chcete-li použít generovaný soubor XML pro použití s funkcí [IntelliSense,](/visualstudio/ide/using-intellisense) nechte název souboru XML stejný jako sestavení, které chcete podporovat, a poté se ujistěte, že soubor XML je ve stejném adresáři jako sestavení. Proto při odkazování na sestavení v projektu sady Visual Studio je nalezen také soubor XML. Další informace naleznete [v tématu Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and For more information.  
  
 Pokud kompilujete s `file` [-target:module](./target-module-compiler-option.md), bude obsahovat \<sestavení>\</assembly> značky určující název souboru obsahujícímanifest sestavení pro výstupní soubor kompilace.  
  
> [!NOTE]
> Možnost -doc platí pro všechny vstupní soubory; nebo, pokud je nastavena v nastavení projektu, všechny soubory v projektu. Chcete-li zakázat upozornění týkající se poznámek k dokumentaci pro určitý soubor nebo část kódu, použijte [#pragma upozornění](../preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Způsoby generování dokumentace z komentářů v kódu najdete v [tématu Doporučené značky pro komentáře k dokumentaci.](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na kartu **Sestavení.**  
  
3. Upravte vlastnost **souboru dokumentace XML.**  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
