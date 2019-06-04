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
ms.openlocfilehash: 703ebcf93af77be2d0034bcd99fab397d7729374
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487002"
---
# <a name="64-bit-applications"></a>64bitové aplikace
Když kompilujete aplikace, můžete určit, že se má spustit v operačním systému Windows 64-bit buď jako nativní aplikaci nebo v modulu WOW64 (Windows 32-bit na Windows 64-bit). Subsystém WOW64 je prostředí kompatibility, která umožňuje 32-bit aplikaci pro spuštění v 64bitovém systému. Subsystém WOW64 je součástí všech 64bitové verze operačního systému Windows.  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a>Spuštění 32bitové vs. 64bitové aplikace na Windows  
 Všechny aplikace, které jsou založené na rozhraní .NET Framework 1.0 nebo 1.1 jsou považovány za 32bitové aplikace na 64bitový operační systém a jsou vždy spouštěny pod WOW64 a 32bitová verze common language runtime (CLR). 32bitových aplikací, které jsou založené na rozhraní .NET Framework 4 nebo novější verze také spuštěna v modulu WOW64 v 64bitových systémech.  
  
 Visual Studio nainstaluje 32bitová verze modulu CLR na x x86 počítače a 32bitové verze i odpovídající 64bitovou verzi modulu CLR v počítači Windows 64-bit. (Protože Visual Studio je 32bitová aplikace, když se nainstaluje na 64bitový systém, běží pod WOW64.)  
  
> [!NOTE]
>  Z důvodu návrhu x86 emulace a subsystém WOW64 pro rodiny procesorů Itanium aplikace jsou omezeny na provádění na jeden procesor. Tyto faktory snížit výkon a škálovatelnost 32bitových aplikací rozhraní .NET Framework, které běží na systémy s procesorem Itanium. Doporučujeme použít rozhraní .NET Framework 4, která zahrnuje nativní 64bitová podpora pro systémy s procesorem Itanium, vyšší výkon a škálovatelnost.  
  
 Ve výchozím nastavení když spustíte 64bitové spravované aplikace v operačním systému Windows 64-bit, můžete vytvořit objekt více než 2 gigabajty (GB). V rozhraní .NET Framework 4.5, ale můžete tento limit zvýšit.  Další informace najdete v tématu [ \<gcAllowVeryLargeObjects > element](../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md).  
  
 Mnoho sestavení spustit stejně jako na modul CLR 32bitová verze a 64bitová verze CLR. Nicméně některé programy může chovat jinak, v závislosti na modulu CLR, pokud obsahují jeden nebo více z následujících akcí:  
  
- Struktury, které obsahují členy, které se mění velikost podle platformy (například libovolný typ ukazatele).  
  
- Aritmetika ukazatele, který obsahuje konstantní velikostí.  
  
- Nesprávný platformu vyvolání nebo deklarace modelu COM, které používají `Int32` pro popisovače místo `IntPtr`.  
  
- Kód, který přetypování `IntPtr` k `Int32`.  
  
 Další informace o vytvoření portu 32bitové aplikace ke spuštění v 64bitovém modulu CLR najdete v tématu [přenesení 32bitového spravovaného kódu na 64bitovou verzi](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973190(v=msdn.10)).  
  
## <a name="general-64-bit-programming-information"></a>Obecné informace o 64bitovém programování  
 Obecné informace o 64bitové programování najdete v následujících dokumentech:  
  
- Další informace o 64bitové verzi modulu CLR v počítači Windows 64-bit, najdete v článku [středisko pro vývojáře rozhraní .NET Framework](https://go.microsoft.com/fwlink/?LinkId=37079) na webu MSDN.  
  
- V [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] dokumentaci najdete v tématu [Průvodce programováním pro Windows 64-bit](https://go.microsoft.com/fwlink/p/?LinkId=253512).  
  
- Informace o tom, jak stáhnout 64bitovou verzi modulu CLR najdete v tématu [rozhraní .NET Framework Developer Center stáhne](https://go.microsoft.com/fwlink/?LinkId=50953) na webu MSDN.  
  
- Informace o Visual Studio – podpora pro vytváření 64bitových aplikací najdete v tématu [podporu služby Visual Studio IDE 64-Bit](/visualstudio/ide/visual-studio-ide-64-bit-support).  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a>Podpora kompilátoru pro vytváření 64bitových aplikací  
 Ve výchozím nastavení, při použití rozhraní .NET Framework a začít vytvářet aplikace pro 32bitové nebo 64bitové počítače, aplikace bude spuštěna na 64bitovém počítači jako nativní aplikaci (tedy ne v modulu WOW64). V následující tabulce jsou uvedeny dokumenty, které popisují, jak použít kompilátory sady Visual Studio k vytvoření 64bitových aplikací, které se spustí jako nativní v prostředí WOW64, nebo obojí.  
  
|Kompilátor|– možnost kompilátoru|  
|--------------|---------------------|  
|Visual Basic|[/ Platform (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/platform.md)|  
|Visual C#|[/ Platform (možnosti kompilátoru C#)](~/docs/csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|Visual C++|Můžete vytvořit více platforem, aplikace Microsoft intermediate language (MSIL) s použitím **/CLR: safe**. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).<br /><br /> Visual C++ obsahuje samostatný kompilátor pro jednotlivé operační systémy 64-bit. Další informace o tom, jak používat Visual C++ vytvářet nativní aplikace, které běží v operačním systému Windows 64-bit, naleznete v tématu [64bitové programování](/cpp/build/configuring-programs-for-64-bit-visual-cpp).|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a>Určení stavu souboru EXE nebo DLL  
 Chcete-li zjistit, zda souboru .exe nebo .dll soubor je určen ke spouštění jenom na konkrétní platformě nebo v modulu WOW64, použijte [CorFlags.exe (corflags – převodní nástroj)](../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md) bez parametrů. CorFlags.exe můžete také použít ke změně stavu platformy souboru .exe nebo .dll soubor. Záhlaví modulu CLR sestavení sady Visual Studio obsahuje verzi modulu runtime hlavní číslo nastavená na hodnotu 2 a dílčí modul runtime verze číslo nastavené na 5. Aplikace, které mají dílčí modul runtime verze nastavena na hodnotu 0 jsou považovány za starší verze aplikací a jsou vždy spouštěny v modulu WOW64.  
  
 Chcete-li programově odeslat dotaz s příponou .exe nebo .dll, které chcete zobrazit, zda je určená ke spuštění pouze na konkrétní platformě nebo v modulu WOW64, použijte <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=nameWithType> metody.
