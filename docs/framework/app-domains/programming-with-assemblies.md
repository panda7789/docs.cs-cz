---
title: Programování se sestaveními
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f427e2260fb26be7db0a29c47f38a3cb32dd34e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921423"
---
# <a name="programming-with-assemblies"></a>Programování se sestaveními
Sestavení jsou stavebními bloky .NET Framework; tvoří základní jednotku nasazení, řízení verze, opětovné použití, rozsah aktivace a oprávnění zabezpečení. Sestavení poskytuje modulu CLR (Common Language Runtime) informace, které požaduje pro zjištění typu implementace. Jedná se o kolekci typů a prostředků, které jsou sestaveny tak, aby spolupracovaly a tvořily logickou jednotku funkcí. V modulu runtime neexistuje typ mimo kontext sestavení.  
  
 Tato část popisuje, jak vytvořit moduly, vytvořit sestavení z modulů, vytvořit pár klíčů a podepsat sestavení se silným názvem a nainstalovat sestavení do globální mezipaměti sestavení (GAC). Kromě toho tato část popisuje, jak použít [jazyk MSIL Disassembler (Ildasm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) k zobrazení informací o manifestu sestavení.  
  
> [!NOTE]
> Počínaje verzí 2,0 .NET Framework modul runtime nenačte sestavení, které bylo zkompilováno s verzí .NET Framework, která má vyšší číslo verze než aktuálně načtený modul runtime. To platí pro kombinaci hlavních a vedlejších součástí čísla verze.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 Poskytuje přehled o jednom souboru a vícesouborové sestavení.  
  
 [Názvy sestavení](../../../docs/framework/app-domains/assembly-names.md)  
 Poskytuje přehled o pojmenovávání sestavení.  
  
 [Postupy: Určení plně kvalifikovaného názvu sestavení](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Popisuje, jak určit plně kvalifikovaný název sestavení.  
  
 [Spouštění internetových aplikací v režimu plné důvěryhodnosti](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Popisuje, jak zadat starší zásady zabezpečení pro sestavení s úplným vztahem důvěryhodnosti pro sdílenou složku v intranetu.  
  
 [Umístění sestavení](../../../docs/framework/app-domains/assembly-location.md)  
 Poskytuje přehled o tom, kde najít sestavení.  
  
 [Postupy: Sestavení jednoho souboru sestavení](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Popisuje, jak vytvořit sestavení s jedním souborem.  
  
 [Vícesouborová sestavení](../../../docs/framework/app-domains/multifile-assemblies.md)  
 Popisuje důvody pro vytváření vícesouborového sestavení.  
  
 [Postupy: Sestavení vícesouborového sestavení](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Popisuje, jak vytvořit vícesouborové sestavení.  
  
 [Nastavování atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Popisuje atributy sestavení a jejich nastavení.  
  
 [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 Popisuje, jak a proč podepsat sestavení silným názvem a obsahuje postupy pro témata.  
  
 [Zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Popisuje, jak zpozdit podpis sestavení.  
  
 [Práce se sestaveními a s globální pamětí sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Popisuje, jak a proč přidat sestavení do globální mezipaměti sestavení (GAC) a obsahuje postupy pro témata.  
  
 [Postupy: Zobrazit obsah sestavení](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Popisuje, jak použít jazyk MSIL Disassembler (Ildasm. exe) k zobrazení obsahu sestavení.  
  
 [Předávání typů v modulu Common Language Runtime](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Popisuje, jak použít přesměrování typu k přesunutí typu do jiného sestavení bez přerušení stávajících aplikací.  
  
## <a name="reference"></a>Reference  
 <xref:System.Reflection.Assembly>  
 Třída .NET Framework, která představuje sestavení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: Získání informací o typu a členu ze sestavení](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Popisuje, jak programově získat typ a další informace ze sestavení.  
  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Poskytuje koncepční přehled sestavení společného jazykového modulu runtime.  
  
 [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md)  
 Poskytuje přehled vazby sestavení a <xref:System.Reflection.AssemblyVersionAttribute> atributů a. <xref:System.Reflection.AssemblyInformationalVersionAttribute>  
  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Popisuje způsob, jakým modul runtime určuje, které sestavení se má použít ke splnění požadavku vazby.  
  
 [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Popisuje způsob použití třídy reflexe k získání informací o sestavení.
