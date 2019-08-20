---
title: -warnaserror – (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 66c78ee56c9d5153b5b878b2e695ad4ee6bffe0b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606247"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror – (C# možnosti kompilátoru)
Parametr **-warnaserror – +** zpracovává všechna upozornění jako chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Poznámky  
 Všechny zprávy, které by byly obvykle hlášeny jako upozornění, jsou místo toho hlášeny jako chyby a proces sestavení se zastaví (nejsou sestaveny žádné výstupní soubory).  
  
 Ve výchozím nastavení je **-warnaserror –-** v platnosti, což způsobí, že upozornění nebrání generování výstupního souboru. **-warnaserror –** , který je stejný jako **-warnaserror – +** , způsobí, že upozornění budou považována za chyby.  
  
 Případně, pokud chcete, aby bylo možné považovat jenom několik specifických upozornění jako chyby, můžete zadat čárkami oddělený seznam čísel upozornění, které se budou považovat za chyby.  
  
 Pomocí [-warn](./warn-compiler-option.md) určete úroveň upozornění, která má kompilátor zobrazovat. Pomocí [-Upozornění](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Upravte vlastnost **považovat upozornění jako chybu** .  
  
 Chcete-li nastavit tuto možnost kompilátoru programově <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>, přečtěte si téma.  
  
## <a name="example"></a>Příklad  
 Kompilovat `in.cs` a nechat kompilátor zobrazovat žádná upozornění:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
