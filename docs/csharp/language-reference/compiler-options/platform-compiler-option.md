---
title: "-platform (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: "46"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d03e12ae60b9a0145dcb58765ae00f756f84ca56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="platform-c-compiler-options"></a>/platform (Možnosti kompilátoru C#)
Určuje, která verze common language runtime (CLR) můžete spustit sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/platform:string  
```  
  
#### <a name="parameters"></a>Parametry  
 `string`  
 anycpu (výchozí), anycpu32bitpreferred, ARM, x 64, x86 nebo Itanium.  
  
## <a name="remarks"></a>Poznámky  
  
-   **anycpu** (výchozí) zkompiluje vaše sestavení pro spouštěn na libovolné platformě. Vaše aplikace běží jako 64bitový proces kdykoli je to možné a spadne zpět na 32-bit v případě pouze tento režim je k dispozici.  
  
-   **anycpu32bitpreferred** zkompiluje vaše sestavení pro spouštěn na libovolné platformě. Vaše aplikace běží v režimu 32-bit v systémech, které podporují 64bitové a 32bitové aplikace. Tato možnost jenom pro projekty můžete zadat cílených rozhraní .NET Framework 4.5.  
  
-   **ARM** zkompiluje vaše sestavení pro spuštění v počítači, který má procesor Advanced RISC Machine (ARM).  
  
-   **x64** zkompiluje vaše sestavení pro modul common language runtime 64-bit spustit na počítači, který podporuje AMD64 nebo EM64T sada instrukcí.  
  
-   **x86** zkompiluje vaše sestavení ke spuštění x86 kompatibilní, 32bitová verze modulu CLR.  
  
-   **Itanium** zkompiluje vaše sestavení, které se má spustit modul common language runtime 64-bit do počítače s procesorem Itanium.  
  
 64bitová verze operačního systému Windows:  
  
-   Sestavení kompilovat s **/platform:x 86** spustit na 32bitová verze modulu CLR spuštěna pod WOW64.  
  
-   Knihovny DLL kompilovat s **/platform:anycpu** spouští ve stejném modulu CLR jako proces, do kterého je načten.  
  
-   Spustitelné soubory, které jsou kompilovat s **/platform:anycpu** spustit na 64-bit CLR.  
  
-   Spustitelné soubory kompilovat s **/platform:anycpu32bitpreferred** spustit na 32bitová verze modulu CLR.  
  
 **Anycpu32bitpreferred** nastavení je platná pouze pro spustitelný soubor (. Soubory EXE) ale vyžaduje rozhraní .NET Framework 4.5.  
  
 Další informace o vývoji aplikace ke spuštění v operačním systému Windows 64-bit najdete v tématu [64bitové aplikace](../../../framework/64-bit-apps.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete **vlastnosti** stránky pro projekt.  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Změnit **Cílová platforma** vlastnost a pro projekty, které cílí na rozhraní .NET Framework 4.5, zaškrtněte nebo zrušte **raději 32bitové** zaškrtávací políčko.  
  
 **Všimněte si, / Platform** není k dispozici ve vývojovém prostředí Visual C# Express.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat **/Platform** můžete určit, že aplikace měly být spuštěny pomocí modulu CLR 64bitová verze 64bitová verze operačního systému Windows.  
  
```console  
csc /platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
