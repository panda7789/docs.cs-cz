---
title: -warnaserror (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 7d43941629e933ac5a9e9c9d6a1388b6194f8d99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503477"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (C# Možnosti kompilátoru)
Možnost **-warnaserror+** považuje všechna upozornění za chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Poznámky  
 Všechny zprávy, které by obvykle být hlášeny jako upozornění jsou místo toho hlášeny jako chyby a proces sestavení je zastaven (jsou vytvořeny žádné výstupní soubory).  
  
 Ve výchozím nastavení **-warnaserror-** je v platnosti, což způsobí, že upozornění nezabrání generování výstupního souboru. **-warnaserror**, který je stejný jako **-warnaserror+**, způsobí, že upozornění považovat za chyby.  
  
 Volitelně pokud chcete, aby pouze několik konkrétních upozornění bylo považováno za chyby, můžete zadat seznam čísel upozornění oddělených čárkami, který bude považován za chyby. Sadu všech upozornění nullability lze zadat s **nullable zkratka.**
  
 Pomocí [-warn](./warn-compiler-option.md) určete úroveň upozornění, kterou má kompilátor zobrazit. Pomocí [funkce -nowarn](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Sestavení.**  
  
3. Upravte **vlastnost Považovat upozornění za chyby.**  
  
 Chcete-li tuto možnost kompilátoru nastavit programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` a mít kompilátor zobrazit žádná upozornění:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
