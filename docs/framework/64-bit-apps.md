---
title: "64bitové aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [C++], 64-bit
- 64-bit applications [C++]
- 64-bit programming [C++]
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
caps.latest.revision: "53"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ee85512cde0ce50e6a5c34cc5f6acc531c24bc0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="64-bit-applications"></a>64bitové aplikace
Při kompilaci aplikace, můžete určit, že ji měly být spuštěny v operačním systému Windows 64-bit buď jako nativní aplikace nebo WOW64 (Windows 32-bit na Windows 64-bit). Subsystém WOW64 je kompatibility prostředí umožňující 32bitovou aplikaci spustit v 64bitovém systému. Subsystém WOW64 je zahrnutá ve všech verzích 64bitová verze operačního systému Windows.  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a>Spuštění 32bitové vs. 64bitové aplikace v systému Windows  
 Všechny aplikace, které jsou postavené na rozhraní .NET Framework 1.0 nebo 1.1 se považují za 32bitové aplikace na 64bitový operační systém a jsou vždy provést v rámci WOW64 a 32-bit common language runtime (CLR). 32bitové aplikace, které jsou vytvořené na [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)] nebo novější verze se také spustit WOW64 v 64bitových systémech.  
  
 Visual Studio nainstaluje 32bitovou verzi modulu CLR na x86 počítače a 32bitová verze i příslušné 64bitovou verzi modulu CLR na počítači se systémem Windows 64-bit. (Vzhledem k Visual Studio 32bitovou aplikaci, když je nainstalován na 64bitový systém, jeho spuštění ve WOW64.)  
  
> [!NOTE]
>  Vzhledem k tomu, x86 emulace a subsystém WOW64 pro třídu procesoru pro procesory Itanium, jsou aplikace s omezeným přístupem k provádění na jeden procesor. Tyto faktory snížit výkon a škálovatelnost 32bitové aplikace rozhraní .NET Framework, které běží na systémy s procesorem Itanium. Doporučujeme vám, že používáte [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)], což zahrnuje nativní podpora 64bitových technologií, pro systémy s procesorem Itanium, vyšší výkon a škálovatelnost.  
  
 Ve výchozím nastavení když spustíte spravované aplikaci 64-bit 64bitová verze operačního systému Windows, můžete vytvořit objekt více než 2 gigabajty (GB). Však [!INCLUDE[net_v45](../../includes/net-v45-md.md)], můžete zvýšit tento limit.  Další informace najdete v tématu [ \<gcallowverylargeobjects – > element](../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md).  
  
 Mnoho sestavení spustit stejně jako na CLR 32bitové a 64bitové verze modulu CLR. Ale některé programy mohou chovat jinak, v závislosti na modulu CLR, pokud budou obsahovat jedno nebo více z následujících akcí:  
  
-   Struktury, které obsahují členy, kteří změnit velikost v závislosti na platformě (například jakýkoli typ ukazatele).  
  
-   Aritmetika ukazatele, který zahrnuje konstantní velikosti.  
  
-   Nesprávný platformy vyvolání nebo COM deklarace, které používají `Int32` pro obslužné rutiny místo `IntPtr`.  
  
-   Kód, který vrhá `IntPtr` k `Int32`.  
  
 Další informace o tom, jak portu 32bitová aplikace ke spuštění na 64-bit CLR najdete v tématu [migraci 32bitový spravovaného kódu na 64bitovou verzi](https://msdn.microsoft.com/library/ms973190.aspx).  
  
## <a name="general-64-bit-programming-information"></a>Obecné informace o 64bitovém programování  
 Obecné informace o 64bitové programování najdete v následujících dokumentech:  
  
-   Další informace o 64bitové verzi modulu CLR na počítači se systémem Windows 64-bit, najdete v článku [rozhraní .NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=37079) na webu MSDN.  
  
-   V [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] dokumentaci najdete v tématu [Průvodce programováním pro 64bitový systém Windows](http://go.microsoft.com/fwlink/p/?LinkId=253512).  
  
-   Informace o tom, jak stáhnout 64bitovou verzi modulu CLR najdete v tématu [rozhraní .NET Framework Developer Center stáhne](http://go.microsoft.com/fwlink/?LinkId=50953) na webu MSDN.  
  
-   Informace o podpoře Visual Studio pro vytváření aplikací pro 64bitové najdete v tématu [podporu Visual Studio IDE 64-Bit](http://msdn.microsoft.com/library/b08ff3ad-c6fd-468f-94d5-01a61aab6833).  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a>Podpora kompilátoru pro vytváření 64bitových aplikací  
 Ve výchozím nastavení, pokud používáte rozhraní .NET Framework pro vytvoření aplikace na 32-bit nebo 64bitový počítač, bude aplikace spuštěná na 64bitovém počítači jako nativní aplikaci (tedy ne WOW64). Následující tabulka uvádí dokumenty, které popisují, jak se kompilátory Visual Studio k vytvoření 64bitové aplikace, které se spustí jako nativní pod WOW64, nebo obojí.  
  
|Kompilátoru|– Možnost kompilátoru|  
|--------------|---------------------|  
|Visual Basic|[/ Platform (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/platform.md)|  
|Visual C#|[/ Platform (možnosti kompilátoru C#)](~/docs/csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|Visual C++|Můžete vytvořit vznikl platformy, aplikací (MSIL intermediate language) společnosti Microsoft pomocí **/CLR: safe**. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).<br /><br /> Visual C++ obsahuje samostatné kompilátoru pro každý 64bitový operační systém. Další informace o tom, jak používat Visual C++ vytvářet nativní aplikace, které běží na operačním systémem Windows 64-bit najdete v tématu [64bitové programování](http://msdn.microsoft.com/library/h2k70f3s\(v=vs.80\)).|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a>Určení stavu souboru EXE nebo DLL  
 Chcete-li zjistit, zda je určená souboru .exe nebo .dll soubor spustit pouze na konkrétní platformu nebo WOW64, použijte [CorFlags.exe (corflags – převodní nástroj)](../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md) bez použití možností. CorFlags.exe můžete taky změnit stav platformy souboru .exe nebo .dll. Hlavička CLR sestavení sady Visual Studio obsahuje hlavní runtime verze číslo nastavená na hodnotu 2 a číslo sada menší runtime verze 5. Aplikace, které mají menší runtime verze nastavena na hodnotu 0, se považují za starší verze aplikace a jsou vždy provést WOW64.  
  
 K dotazování prostřednictvím kódu programu příponou .exe nebo .dll, které chcete zobrazit, zda smyslem je spustit pouze na konkrétní platformu nebo WOW64, použijte <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=nameWithType> metoda.
