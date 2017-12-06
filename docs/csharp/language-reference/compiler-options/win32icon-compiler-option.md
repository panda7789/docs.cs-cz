---
title: "-win32icon (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 356502b8528e22a5b5ff9a28a3f82d5f9c0a72f9
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2017
---
# <a name="win32icon-c-compiler-options"></a>/win32icon (Možnosti kompilátoru C#)
**/Win32icon** možnost vloží soubor .ico, který do výstupního souboru, který poskytuje výstupní soubor požadovaný vzhled v Průzkumníkovi souborů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Soubor .ico, který chcete přidat do výstupního souboru.  
  
## <a name="remarks"></a>Poznámky  
 Soubor .ico, který může být vytvořen pomocí [kompilátor prostředků](https://msdn.microsoft.com/library/aa381042.aspx). Kompilátor prostředků je vyvolán při kompilaci Visual C++ program; soubor .ico, který je vytvořen ze souboru .rc.  
  
 V tématu [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (pro referenční dokumentace) nebo [/Resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (pro připojení) souboru prostředků rozhraní .NET Framework. V tématu [/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) .res soubor naimportovat.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **aplikace** stránku vlastností.  
  
3.  Změnit **ikona aplikace** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` a připojte soubor .ico `rf.ico` k vytvoření `in.exe`:  
  
```console  
csc /win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
