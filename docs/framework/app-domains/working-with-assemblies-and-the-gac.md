---
title: Práce se sestaveními a s globální pamětí sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0331e0ad30743d5f0bba125e8e61e636e1c2a5be
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053025"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a>Práce se sestaveními a s globální pamětí sestavení

Pokud máte v úmyslu sdílet sestavení mezi několika aplikacemi, můžete jej nainstalovat do globální mezipaměti sestavení (GAC). Každý počítač, ve kterém je nainstalován modul CLR (Common Language Runtime), má tuto mezipaměť kódu pro všechny počítače. Globální mezipaměť sestavení ukládá sestavení speciálně určená pro sdílení několika aplikacemi v počítači. Sestavení musí mít silný název, který se má nainstalovat do globální mezipaměti sestavení (GAC).  
  
> [!NOTE]
> Sestavení umístěná v globální mezipaměti sestavení (GAC) musí mít stejný název sestavení a název souboru (včetně přípony názvu souboru). Například sestavení s názvem sestavení myAssembly musí mít název souboru buď myAssembly. exe, nebo myAssembly. dll.  
  
Sestavení byste měli sdílet tak, že je nainstalujete do globální mezipaměti sestavení (GAC) pouze v případě potřeby. Obecné pokyny, udržujte závislosti sestavení soukromě a vyhledejte sestavení v adresáři aplikace, pokud není explicitně požadováno sdílení sestavení. Kromě toho není nutné instalovat sestavení do globální mezipaměti sestavení (GAC), aby byly přístupné pro zprostředkovatele komunikace s objekty COM nebo nespravovaný kód.  
  
Existuje několik důvodů, proč je vhodné nainstalovat sestavení do globální mezipaměti sestavení (GAC):  
  
- Sdílené umístění.  
  
     Sestavení, která by měla být použita aplikacemi, lze umístit do globální mezipaměti sestavení (GAC). Například pokud má všechny aplikace použít sestavení umístěné v globální mezipaměti sestavení (GAC), do souboru Machine. config, který přesměrovává odkazy na sestavení, lze přidat příkaz zásad verze.  
  
- Zabezpečení souborů.  
  
     Správci často chrání adresář kořenová_složka_systému pomocí seznamu Access Control (ACL) pro řízení přístupu pro zápis a spouštění. Vzhledem k tomu, že je globální mezipaměť sestavení (GAC) nainstalována v adresáři kořenová_složka_systému, zdědí seznam řízení přístupu daného adresáře. Doporučujeme, aby odstraňování souborů z globální mezipaměti sestavení bylo povoleno pouze uživatelům s oprávněními správce.  
  
- Souběžná Správa verzí.  
  
     V globální mezipaměti sestavení (GAC) je možné uchovávat více kopií sestavení se stejným názvem, ale různé informace o verzi.  
  
- Další umístění pro hledání.  
  
     Modul CLR (Common Language Runtime) kontroluje globální mezipaměť sestavení (GAC) pro sestavení, které odpovídá žádosti o sestavení, před prošetřením nebo použitím informací o základu kódu v konfiguračním souboru.  
  
 Všimněte si, že existují scénáře, kde explicitně nechcete instalovat sestavení do globální mezipaměti sestavení (GAC). Pokud umístíte jedno ze sestavení, která tvoří aplikaci do globální mezipaměti sestavení (GAC), nelze již aplikaci replikovat nebo nainstalovat pomocí příkazu XCOPY ke zkopírování adresáře aplikace. V takovém případě musíte také přesunout sestavení do globální mezipaměti sestavení (GAC).  
  
## <a name="in-this-section"></a>V tomto oddílu  
[Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC)](install-assembly-into-gac.md)  
Popisuje způsoby instalace sestavení do globální mezipaměti sestavení.  
  
[Postupy: Zobrazit obsah globální mezipaměti sestavení (GAC)](how-to-view-the-contents-of-the-gac.md)  
Vysvětluje, jak použít nástroj [Gacutil. exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) k zobrazení obsahu globální mezipaměti sestavení (GAC).  
  
[Postupy: Odebrání sestavení z globální mezipaměti sestavení (GAC)](how-to-remove-an-assembly-from-the-gac.md)  
Vysvětluje, jak použít nástroj [Gacutil. exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) k odebrání sestavení z globální mezipaměti sestavení (GAC).  
  
[Používání obsluhovaných komponent s globální pamětí sestavení](use-serviced-components-with-the-gac.md)  
Vysvětluje, proč se obsluhované komponenty (spravované komponenty modelu COM+) měly umístit do globální mezipaměti sestavení (GAC).  
  
## <a name="related-sections"></a>Související oddíly  

[Vytváření sestavení](../../standard/assembly/create.md)  
Poskytuje přehled o vytváření sestavení.  
  
[Globální mezipaměť sestavení](gac.md)  
Popisuje globální mezipaměť sestavení (GAC).  
  
[Postupy: Zobrazit obsah sestavení](../../standard/assembly/view-contents.md)  
Vysvětluje, jak používat nástroj [Ildasm. exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) k zobrazení informací o jazyce MSIL (Microsoft Intermediate Language) v sestavení.  
  
[Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)  
Popisuje, jak modul CLR (Common Language Runtime) vyhledá a načte sestavení, která tvoří vaši aplikaci.  
  
[Programování se sestaveními](../../standard/assembly/program.md)  
Popisuje sestavení, stavební bloky spravovaných aplikací.
