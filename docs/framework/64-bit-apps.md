---
title: 64bitové aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- applications [C++], 64-bit
- 64-bit applications [C++]
- 64-bit programming [C++]
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ff02c5856e4ee48c8e5cf375cc68d92c76737c7
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988395"
---
# <a name="64-bit-applications"></a>64bitové aplikace
Když kompilujete aplikaci, můžete určit, že má běžet v operačním systému Windows 64 jako nativní aplikace nebo v modulu WOW64 (Windows 32-bit v systému Windows 64-bit). Subsystém WOW64 je prostředí kompatibility, které umožňuje spuštění 32 aplikace v systému 64. Subsystém WOW64 je součástí všech 64 bitových verzí operačního systému Windows.  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a>Spouštění 32 bitů vs. 64 – bitové aplikace ve Windows  
 Všechny aplikace, které jsou postavené na .NET Framework 1,0 nebo 1,1, se považují za 32 aplikace 64 v 16bitovém operačním systému a jsou vždy spouštěny v prostředí WOW64 a 32 v modulu CLR (Common Language Runtime). 32 bitové aplikace, které jsou postavené na .NET Framework 4 nebo novějších verzích, se spouštějí také v modulu WOW64 v systémech 64.  
  
 Visual Studio nainstaluje 32 verzi modulu CLR na počítač s procesorem x86 a jak 32 verzi, tak i 64 příslušnou jazykovou verzi modulu CLR na počítač s 64 bitovými systémy Windows. (Vzhledem k tomu, že Visual Studio je 32 aplikace, když je nainstalovaná na 64 systému, běží pod WOW64.)  
  
> [!NOTE]
> Vzhledem k tomu, že se jedná o návrh emulace x86 a subsystému WOW64 pro rodinu procesorů s procesorem Itanium, jsou aplikace omezené na spouštění v jednom procesoru. Tyto faktory omezují výkon a škálovatelnost 32 .NET Framework aplikací, které běží na systémech založených na procesorech Itanium. Pro zvýšení výkonu a škálovatelnosti doporučujeme použít .NET Framework 4, která zahrnuje nativní podporu 64 pro systémy s procesorem Itanium.  
  
 Ve výchozím nastavení platí, že při spuštění 64 spravované aplikace na 64 operačním systému Windows můžete vytvořit objekt, který nemá více než 2 gigabajty (GB). V .NET Framework 4,5 však můžete tento limit zvýšit.  Další informace naleznete v [ \<tématu gcAllowVeryLargeObjects > element](../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md).  
  
 Mnoho sestavení běží stejným způsobem na 32 CLR a 64-bit CLR. Některé programy se však mohou chovat jinak, v závislosti na modulu CLR, pokud obsahují jednu nebo více následujících možností:  
  
- Struktury, které obsahují členy, které mění velikost v závislosti na platformě (například libovolný typ ukazatele).  
  
- Aritmetický ukazatel, který obsahuje konstantní velikosti.  
  
- Nesprávné vyvolání platformy nebo deklarace com, které `Int32` používají pro popisovače `IntPtr`místo.  
  
- Kód, který `IntPtr` se přetypování na `Int32`.  
  
 Další informace o tom, jak nasměrovat 32-bitovou aplikaci pro spuštění na 64 modulu CLR, najdete v tématu [migrace 32-bitového spravovaného kódu na 64](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973190(v=msdn.10)).  
  
## <a name="general-64-bit-programming-information"></a>Obecné informace o 64bitovém programování  
 Obecné informace o 64 programování najdete v následujících dokumentech:  
  
- Další informace o 64 verze modulu CLR na počítači se systémem Windows na 64 naleznete v [centru pro vývojáře .NET Framework](https://go.microsoft.com/fwlink/?LinkId=37079) na webu MSDN.  
  
- V dokumentaci k Windows SDK najdete informace v tématu [Průvodce programováním pro 64-bit Windows](https://go.microsoft.com/fwlink/p/?LinkId=253512).  
  
- Informace o tom, jak stáhnout 64 verze modulu CLR, najdete v tématu [.NET Framework stažení centra pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=50953) na webu MSDN.  
  
- Informace o podpoře sady Visual Studio pro vytváření 64 aplikací naleznete v tématu [Podpora sady Visual Studio IDE pro 64](/visualstudio/ide/visual-studio-ide-64-bit-support).  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a>Podpora kompilátoru pro vytváření 64bitových aplikací  
 Ve výchozím nastavení platí, že když použijete .NET Framework k sestavení aplikace na 32 nebo na 64 počítači, aplikace se spustí v počítači s 64 jako nativní aplikaci (tj. není pod WOW64). V následující tabulce jsou uvedeny dokumenty, které vysvětlují použití kompilátorů sady Visual Studio k vytváření 64 aplikací, které budou spouštěny jako nativní, v modulu WOW64 nebo v obou.  
  
|Přepínač|Možnost kompilátoru|  
|--------------|---------------------|  
|Visual Basic|[/Platform (Visual Basic)](../visual-basic/reference/command-line-compiler/platform.md)|  
|Visual C#|[/Platform (C# možnosti kompilátoru)](../csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|Visual C++|Pomocí **/clr: Safe**můžete vytvářet aplikace nezávislá platforem a aplikací jazyka MSIL (Microsoft Intermediate Language). Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](/cpp/build/reference/clr-common-language-runtime-compilation).<br /><br /> Vizuál C++ obsahuje samostatný kompilátor pro každý 64 operační systém. Další informace o tom, jak používat vizuál C++ k vytváření nativních aplikací, které běží na 64 operačním systému Windows, najdete v tématu [64-bitové programování](/cpp/build/configuring-programs-for-64-bit-visual-cpp).|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a>Určení stavu souboru EXE nebo DLL  
 Chcete-li zjistit, zda je soubor. exe nebo soubor. dll určen pro spuštění pouze na konkrétní platformě nebo v modulu WOW64, použijte [nástroj CorFlags. exe (CorFlags Conversion Tool)](../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md) bez možností. Pomocí nástroje CorFlags. exe můžete také změnit stav platformy souboru. exe nebo souboru. dll. Hlavička CLR sestavení sady Visual Studio má hlavní číslo verze modulu runtime nastavenou na hodnotu 2 a vedlejší číslo verze modulu runtime nastaveno na hodnotu 5. Aplikace, které mají vedlejší verzi modulu runtime nastavenou na hodnotu 0, jsou považovány za starší aplikace a jsou vždy spouštěny v prostředí WOW64.  
  
 Chcete-li se programově dotazovat na soubor. exe nebo. dll, aby bylo možné spustit pouze konkrétní platformu nebo v modulu WOW64, použijte <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=nameWithType> metodu.
