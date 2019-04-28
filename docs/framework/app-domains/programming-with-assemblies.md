---
title: Programování se sestaveními
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6a20a2e678c10157fed7da6f5de9f3ffee0c9ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705542"
---
# <a name="programming-with-assemblies"></a>Programování se sestaveními
Sestavení jsou stavební kameny nástroje rozhraní .NET Framework. tvoří základní jednotku nasazení, správu verzí, opětovného použití, rozsahu platnosti při aktivaci a oprávnění zabezpečení. Sestavení poskytuje modulu CLR (Common Language Runtime) informace, které požaduje pro zjištění typu implementace. Jde o kolekci typů a prostředků, které jsou vytvořené pro spolupracovaly a tvořily logickou jednotku funkčnosti. V modulu runtime neexistuje typ mimo kontext sestavení.  
  
 Tato část popisuje, jak vytvářet moduly, vytvořit sestavení z modulů, vytvořte dvojici klíčů a podepsání sestavení silným názvem a instalace sestavení do globální mezipaměti sestavení. Kromě toho tato část popisuje způsob použití [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zobrazíte informace o manifestu sestavení.  
  
> [!NOTE]
>  Od verze rozhraní .NET Framework verze 2.0, nenačte modul runtime, který byl zkompilován s verzí rozhraní .NET Framework, která má vyšší číslo verze než aktuálně zavedený modul runtime sestavení. To platí pro kombinaci hlavní a vedlejší součásti číslo verze.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 Poskytuje přehled o jeden soubor a vícesouborové sestavení.  
  
 [Názvy sestavení](../../../docs/framework/app-domains/assembly-names.md)  
 Poskytuje přehled o pojmenovávání sestavení.  
  
 [Postupy: Určení plně kvalifikovaného názvu sestavení](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Popisuje, jak určit plně kvalifikovaný název sestavení.  
  
 [Spouštění internetových aplikací v režimu plné důvěryhodnosti](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Popisuje, jak určit starší verze zásad zabezpečení pro plně důvěryhodná sestavení ve sdílené složce intranetu.  
  
 [Umístění sestavení](../../../docs/framework/app-domains/assembly-location.md)  
 Poskytuje přehled o vyhledání sestavení.  
  
 [Postupy: Sestavení s jediným souborem](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Popisuje postup vytvoření jednosouborového sestavení.  
  
 [Vícesouborová sestavení](../../../docs/framework/app-domains/multifile-assemblies.md)  
 Popisuje důvody pro vytvoření vícesouborového sestavení.  
  
 [Postupy: Vytváření vícesouborového sestavení](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Popisuje, jak vytvořit vícesouborové sestavení.  
  
 [Nastavování atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Popisuje atributy sestavení a jejich nastavení.  
  
 [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 Popisuje, jak a proč podepsání sestavení silným názvem a obsahuje témata s postupy.  
  
 [Zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Popisuje, jak zpožděný podpis sestavení.  
  
 [Práce se sestaveními a s globální pamětí sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Popisuje, jak a proč přidávání sestavení do globální mezipaměti sestavení a obsahuje témata s postupy.  
  
 [Postupy: Zobrazení obsahu sestavení](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Popisuje způsob použití jazyka MSIL Disassembler (Ildasm.exe) k zobrazení obsahu sestavení.  
  
 [Předávání typů v modulu Common Language Runtime](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Popisuje, jak používat předávání typů pro přesunutí typu do jiného sestavení bez porušení existujících aplikací.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Reflection.Assembly>  
 Třída rozhraní .NET Framework, která představuje sestavení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: Získávání informací o člen typu a ze sestavení](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Popisuje, jak prostřednictvím kódu programu získání dalších informací o typu a ze sestavení.  
  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Poskytuje koncepční přehled common language runtime sestavení.  
  
 [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md)  
 Obsahuje základní informace o prvku vazby sestavení a <xref:System.Reflection.AssemblyVersionAttribute> a <xref:System.Reflection.AssemblyInformationalVersionAttribute> atributy.  
  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Popisuje, jak modul runtime určuje sestavení, které použije ke splnění požadavků vazby.  
  
 [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Popisuje způsob použití **reflexe** třídy k získání informací o sestavení.
