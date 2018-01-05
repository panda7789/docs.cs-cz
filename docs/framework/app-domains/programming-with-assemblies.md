---
title: "Programování se sestaveními"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46cc7d1be867ff94ca25d0d6ffaaf46a6dc9514b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="programming-with-assemblies"></a>Programování se sestaveními
Sestavení jsou stavebními bloky rozhraní .NET Framework; tvoří základní jednotku nasazení, Správa verzí, opakované použití, aktivaci oborů a oprávnění zabezpečení. Sestavení poskytuje modulu CLR (Common Language Runtime) informace, které požaduje pro zjištění typu implementace. Jedná se o kolekci typů a prostředků, které jsou vytvořeny a společně tvoří logickou jednotku funkčnosti. V modulu runtime neexistuje typ mimo kontext sestavení.  
  
 Tato část popisuje, jak vytvořit moduly, vytvořit sestavení z modulů, vytvořte dvojici klíčů a podepsání sestavení se silným názvem a instalace sestavení do globální mezipaměti sestavení. Kromě toho tato část popisuje postup použití [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) k zobrazení informací o manifestu sestavení.  
  
> [!NOTE]
>  Od verze rozhraní .NET Framework verze 2.0, modul runtime nenačte sestavení, které bylo kompilováno s verzi rozhraní .NET Framework, který má vyšší číslo verze než aktuálně načtených modulu runtime. To platí pro soubor součástí hlavní a vedlejší číslo verze.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 Poskytuje přehled o jeden soubor a vícesouborového sestavení.  
  
 [Názvy sestavení](../../../docs/framework/app-domains/assembly-names.md)  
 Poskytuje přehled o pojmenování sestavení.  
  
 [Postupy: Určení plně kvalifikovaného názvu sestavení](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Popisuje, jak určit plně kvalifikovaný název sestavení.  
  
 [Spouštění internetových aplikací v režimu plné důvěryhodnosti](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Popisuje, jak zadat starší verze zásad zabezpečení pro sestavení plné důvěryhodnosti ve sdílené složce intranetu.  
  
 [Umístění sestavení](../../../docs/framework/app-domains/assembly-location.md)  
 Poskytuje přehled o umístění sestavení.  
  
 [Postupy: Vytváření sestavení s jediným souborem](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Popisuje, jak vytvořit jeden soubor sestavení.  
  
 [Vícesouborová sestavení](../../../docs/framework/app-domains/multifile-assemblies.md)  
 Popisuje důvody pro vytváření vícesouborového sestavení.  
  
 [Postupy: Vytváření vícesouborového sestavení](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Popisuje postup vytvoření vícesouborového sestavení.  
  
 [Nastavování atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Popisuje atributů sestavení a jejich nastavení.  
  
 [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 Popisuje, jak a proč podepsání sestavení se silným názvem a obsahuje témata s postupy.  
  
 [Zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Popisuje postup zpoždění podepsání sestavení.  
  
 [Práce se sestaveními a s globální pamětí sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Popisuje, jak a proč přidat sestavení do globální mezipaměti sestavení a obsahuje témata s postupy.  
  
 [Postupy: Zobrazení obsahu sestavení](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Popisuje, jak používat MSIL Disassembler (Ildasm.exe) k zobrazení obsahu sestavení.  
  
 [Předávání typů v modulu Common Language Runtime](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Popisuje, jak používat předávání typů typu přesunout do jiného sestavení bez porušení existujících aplikací.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Reflection.Assembly>  
 Třída rozhraní .NET Framework, která představuje sestavení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: Získávání informací o typu a členu ze sestavení](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Popisuje, jak programově získat typ a další informace z sestavení.  
  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Poskytuje koncepční přehled common language runtime sestavení.  
  
 [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md)  
 Poskytuje přehled vlastností sestavení – vazby a <xref:System.Reflection.AssemblyVersionAttribute> a <xref:System.Reflection.AssemblyInformationalVersionAttribute> atributy.  
  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Popisuje, jak modul runtime určuje sestavení, které použije ke splnění požadavku vazby.  
  
 [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Popisuje postup použití **reflexe** třída získat informace o sestavení.
