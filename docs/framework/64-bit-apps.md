---
title: 64bitové aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- applications [C++], 64-bit
- 64-bit applications [C++]
- 64-bit programming [C++]
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
ms.openlocfilehash: 90e022d5643dc49ccc5b78d071b3b473c92f0670
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74429661"
---
# <a name="64-bit-applications"></a>64bitové aplikace
Při kompilaci aplikace můžete určit, že by měla být spuštěna v 64bitovém operačním systému Windows buď jako nativní aplikace, nebo v části WOW64 (Windows 32bitv systému Windows 64-bit). WOW64 je kompatibilní prostředí, které umožňuje spuštění 32bitové aplikace v 64bitovém systému. WOW64 je součástí všech 64bitových verzí operačního systému Windows.  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a>Spouštění 32bitových vs. 64bitových aplikací v systému Windows  
 Všechny aplikace, které jsou postaveny na rozhraní .NET Framework 1.0 nebo 1.1 jsou považovány za 32bitové aplikace v 64bitovém operačním systému a jsou vždy spouštěny pod WOW64 a 32bitovým běžným jazykovým runtimem (CLR). 32bitové aplikace, které jsou postaveny na rozhraní .NET Framework 4 nebo novějších verzích, jsou také spuštěny pod WOW64 v 64bitových systémech.  
  
 Visual Studio nainstaluje 32bitovou verzi CLR do počítače x86 a 32bitovou verzi a příslušnou 64bitovou verzi clr v 64bitovém počítači se systémem Windows. (Vzhledem k tomu, že Visual Studio je 32bitová aplikace, když je nainstalována na 64bitovém systému, běží pod WOW64.)  
  
> [!NOTE]
> Vzhledem k návrhu emulace x86 a subsystému WOW64 pro řadu procesorů Itanium jsou aplikace omezeny na spuštění na jednom procesoru. Tyto faktory snižují výkon a škálovatelnost 32bitových aplikací rozhraní .NET Framework, které běží v systémech založených na procesoru Itanium. Doporučujeme použít rozhraní .NET Framework 4, který zahrnuje nativní 64bitovou podporu pro počítače založené na procesoru Itanium, pro zvýšení výkonu a škálovatelnosti.  
  
 Ve výchozím nastavení můžete při spuštění 64bitové spravované aplikace v 64bitovém operačním systému Windows vytvořit objekt o velikosti maximálně 2 gigabajty (GB). V rámci rozhraní .NET Framework 4.5 však můžete tento limit zvýšit.  Další informace naleznete v [ \<gcAllowVeryLargeObjects> element .](./configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)  
  
 Mnoho sestavení běží stejně na 32bitové clr a 64bitové CLR. Některé programy se však mohou chovat odlišně v závislosti na clr, pokud obsahují jednu nebo více z následujících položek:  
  
- Struktury, které obsahují členy, které mění velikost v závislosti na platformě (například libovolný typ ukazatele).  
  
- Aritmetika ukazatele, která obsahuje konstantní velikosti.  
  
- Nesprávné platformy vyvolat nebo `Int32` COM deklarace, `IntPtr`které používají pro popisovače namísto .  
  
- Kód, který `IntPtr` `Int32`přetypována do .  
  
 Další informace o tom, jak portovat 32bitovou aplikaci pro spuštění v 64bitovém clr, naleznete [v tématu Migrace 32bitového spravovaného kódu na 64bitový](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973190(v=msdn.10))kód .  
  
## <a name="general-64-bit-programming-information"></a>Obecné informace o 64bitovém programování  
 Obecné informace o 64bitovém programování naleznete v následujících dokumentech:  
  
- V dokumentaci k sada Windows SDK naleznete [průvodce programováním pro 64bitový systém Windows](/windows/win32/winprog64/programming-guide-for-64-bit-windows).  
  
- Informace o podpoře sady Visual Studio pro vytváření 64bitových aplikací naleznete v [tématu 64bitová podpora aplikace Visual Studio IDE](/visualstudio/ide/visual-studio-ide-64-bit-support).  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a>Podpora kompilátoru pro vytváření 64bitových aplikací  
 Ve výchozím nastavení při použití rozhraní .NET Framework k vytvoření aplikace v 32bitovém nebo 64bitovém počítači bude aplikace spuštěna v 64bitovém počítači jako nativní aplikace (tj. ne pod WOW64). V následující tabulce jsou uvedeny dokumenty, které vysvětlují, jak pomocí kompilátorů sady Visual Studio vytvořit 64bitové aplikace, které budou spuštěny jako nativní, v části WOW64 nebo obojí.  
  
|Kompilátoru|Možnost kompilátoru|  
|--------------|---------------------|  
|Visual Basic|[-platforma (Visual Basic)](../visual-basic/reference/command-line-compiler/platform.md)|  
|Visual C#|[-platforma (Možnosti kompilátoru Jazyka C#)](../csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|Visual C++|Můžete vytvořit platformu agnostik, Microsoft zprostředkující jazyk (MSIL) aplikace pomocí **/clr:safe**. Další informace naleznete v tématu [-clr (Common Language Runtime Compilation)](/cpp/build/reference/clr-common-language-runtime-compilation).<br /><br /> Visual C++ obsahuje samostatný kompilátor pro každý 64bitový operační systém. Další informace o použití jazyka Visual C++ k vytváření nativních aplikací spuštěných v 64bitovém operačním systému Windows naleznete v [tématu 64bitové programování](/cpp/build/configuring-programs-for-64-bit-visual-cpp).|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a>Určení stavu souboru EXE nebo DLL  
 Chcete-li zjistit, zda je soubor EXE nebo DLL určen ke spuštění pouze na určité platformě nebo v části WOW64, použijte [nástroj CorFlags.exe (CorFlags Conversion Tool)](./tools/corflags-exe-corflags-conversion-tool.md) bez možností. Pomocí souboru CorFlags.exe můžete také změnit stav platformy souboru EXE nebo DLL. Hlavička CLR sestavení sady Visual Studio má číslo hlavní verze runtime nastaveno na 2 a číslo dílčí verze runtime nastaveno na 5. Aplikace, které mají dílčí runtime verze nastavena na 0 jsou považovány za starší aplikace a jsou vždy spuštěny pod WOW64.  
  
 Chcete-li programově dotazovat soubor u.exe nebo .dll, abyste zjistili, zda má <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=nameWithType> být spuštěn pouze na určité platformě nebo v části WOW64, použijte metodu.
