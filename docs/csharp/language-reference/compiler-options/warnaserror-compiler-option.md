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
ms.openlocfilehash: 7d43941629e933ac5a9e9c9d6a1388b6194f8d99
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503477"
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
  
 Případně, pokud chcete, aby bylo možné považovat jenom několik specifických upozornění jako chyby, můžete zadat čárkami oddělený seznam čísel upozornění, které se budou považovat za chyby. Sada všech upozornění s hodnotou null se dá zadat s zkráceným **připouštějící hodnotu null** .
  
 Pomocí [-warn](./warn-compiler-option.md) určete úroveň upozornění, která má kompilátor zobrazovat. Pomocí [-Upozornění](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Upravte vlastnost **považovat upozornění jako chybu** .  
  
 Chcete-li nastavit tuto možnost kompilátoru programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.  
  
## <a name="example"></a>Příklad  
 Zkompilovat `in.cs` a nechat kompilátor zobrazovat žádná upozornění:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
