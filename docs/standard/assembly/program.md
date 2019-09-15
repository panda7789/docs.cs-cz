---
title: Program se sestaveními
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03babe701b46eab54a76094c4728af80e6d9911e
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973136"
---
# <a name="program-with-assemblies"></a>Program se sestaveními
Sestavení jsou stavebními bloky .NET Framework; tvoří základní jednotku nasazení, řízení verze, opětovné použití, rozsah aktivace a oprávnění zabezpečení. Sestavení poskytuje modulu CLR (Common Language Runtime) informace, které požaduje pro zjištění typu implementace. Jedná se o kolekci typů a prostředků, které jsou sestaveny tak, aby spolupracovaly a tvořily logickou jednotku funkcí. V modulu runtime neexistuje typ mimo kontext sestavení.  
  
 Tato část popisuje, jak vytvořit moduly, vytvořit sestavení z modulů, vytvořit pár klíčů a podepsat sestavení se silným názvem a nainstalovat sestavení do globální mezipaměti sestavení (GAC). Kromě toho tato část popisuje, jak použít [jazyk MSIL Disassembler (Ildasm. exe)](../../framework/tools/ildasm-exe-il-disassembler.md) k zobrazení informací o manifestu sestavení.  
  
> [!NOTE]
> Počínaje verzí 2,0 .NET Framework modul runtime nenačte sestavení, které bylo zkompilováno s verzí .NET Framework, která má vyšší číslo verze než aktuálně načtený modul runtime. To platí pro kombinaci hlavních a vedlejších součástí čísla verze.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytváření sestavení](create.md)  
 Poskytuje přehled o jednom souboru a vícesouborové sestavení.  
  
 [Názvy sestavení](names.md)  
 Poskytuje přehled o pojmenovávání sestavení.  
  
 [Postupy: Určení plně kvalifikovaného názvu sestavení](find-fully-qualified-name.md)  
 Popisuje, jak určit plně kvalifikovaný název sestavení.  
  
 [Spouštění intranetových aplikací v úplném vztahu důvěryhodnosti](../../framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Popisuje, jak zadat starší zásady zabezpečení pro sestavení s úplným vztahem důvěryhodnosti pro sdílenou složku v intranetu.  
  
 [Umístění sestavení](location.md)  
 Poskytuje přehled o tom, kde najít sestavení.  
  
 [Postupy: Sestavení jednoho souboru sestavení](../../framework/app-domains/build-single-file-assembly.md)  
 Popisuje, jak vytvořit sestavení s jedním souborem.  
  
 [Vícesouborové sestavení](../../framework/app-domains/multifile-assemblies.md)  
 Popisuje důvody pro vytváření vícesouborového sestavení.  
  
 [Postupy: Sestavení vícesouborového sestavení](../../framework/app-domains/build-multifile-assembly.md)  
 Popisuje, jak vytvořit vícesouborové sestavení.  
  
 [Nastavit atributy sestavení](set-attributes.md)  
 Popisuje atributy sestavení a jejich nastavení.  
  
 [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)  
 Popisuje, jak a proč podepsat sestavení silným názvem a obsahuje postupy pro témata.  
  
 [Zpožděný podpis sestavení](delay-sign.md)  
 Popisuje, jak zpozdit podpis sestavení.  
  
 [Práce se sestaveními a globální mezipamětí sestavení](../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Popisuje, jak a proč přidat sestavení do globální mezipaměti sestavení (GAC) a obsahuje postupy pro témata.  
  
 [Postupy: Zobrazit obsah sestavení](view-contents.md)  
 Popisuje, jak použít jazyk MSIL Disassembler (Ildasm. exe) k zobrazení obsahu sestavení.  
  
 [Předávání typů v modulu CLR (Common Language Runtime)](type-forwarding.md)  
 Popisuje, jak použít přesměrování typu k přesunutí typu do jiného sestavení bez přerušení stávajících aplikací.  
  
## <a name="reference"></a>Reference  
 <xref:System.Reflection.Assembly>  
 Třída .NET Framework, která představuje sestavení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: Získání informací o typu a členu ze sestavení](../../framework/reflection-and-codedom/get-type-member-information.md)  
 Popisuje, jak programově získat typ a další informace ze sestavení.  
  
 [Sestavení v .NET](index.md)  
 Poskytuje koncepční přehled sestavení společného jazykového modulu runtime.  
  
 [Správa verzí sestavení](versioning.md)  
 Poskytuje přehled vazby sestavení a <xref:System.Reflection.AssemblyVersionAttribute> atributů a. <xref:System.Reflection.AssemblyInformationalVersionAttribute>  
  
 [Způsob, jakým modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)  
 Popisuje způsob, jakým modul runtime určuje, které sestavení se má použít ke splnění požadavku vazby.  
  
 [Operace](../../framework/reflection-and-codedom/reflection.md)   
 Popisuje způsob použití třídy **reflexe** k získání informací o sestavení.
