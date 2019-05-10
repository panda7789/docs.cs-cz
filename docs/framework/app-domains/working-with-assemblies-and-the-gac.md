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
ms.openlocfilehash: 363410baea1706211acaa639f1704e91230723a8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592747"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a>Práce se sestaveními a s globální pamětí sestavení
Pokud máte v úmyslu sdílení sestavení mezi více aplikacemi, můžete ji nainstalovat do globální mezipaměti sestavení. Každý počítač, kde je nainstalován modul common language runtime obsahuje tuto mezipaměť kódu celého stroje. Globální mezipaměti sestavení ukládá sestavení speciálně určené ke sdílení více aplikacemi v počítači. Sestavení musí mít nainstalovaný v globální mezipaměti sestavení silným názvem.  
  
> [!NOTE]
>  Sestavení do globální mezipaměti sestavení musí mít stejný název sestavení a název souboru (bez přípony názvu souboru). Například sestavení s názvem sestavení myAssembly musí mít název souboru, myAssembly.exe buď myAssembly.dll.  
  
 Sestavení by měly sdílet pomocí instalace do globální mezipaměti sestavení pouze v případě potřeby. V rámci obecných pokynů udržujte soukromé závislosti sestavení a vyhledání sestavení v adresáři aplikace, pokud sdílení sestavení není explicitně vyžadováno. Kromě toho není nutné instalovat sestavení do globální mezipaměti sestavení zajistíte jejich přístupnost COM interop nebo nespravovaného kódu.  
  
 Tady je několik důvodů, proč můžete chtít instalace sestavení do globální mezipaměti sestavení:  
  
- Sdílené umístění.  
  
     Sestavení, které by měly být používány aplikací můžete umístit do globální mezipaměti sestavení. Například zda všechny aplikace by měly používat sestavení v globální mezipaměti sestavení, prohlášením o zásadách verze lze přidat do souboru Machine.config. ten přesměruje odkazy na sestavení.  
  
- Soubor zabezpečení.  
  
     Správci často chrání pomocí seznamu řízení přístupu (ACL) pro řízení zápisu a přístup pro spouštění kořenovou složku. Protože je nainstalována do globální mezipaměti sestavení v kořenové složce dědí seznamu ACL tohoto adresáře. Doporučuje se, že pouze uživatelé s oprávněními správce bude moct odstranit soubory z globální mezipaměti sestavení.  
  
- Správa verzí vedle sebe.  
  
     V globální mezipaměti sestavení může být udržuje několik kopií sestavení se stejným názvem, ale informace o různých verzích.  
  
- Poloha při hledání další.  
  
     Modul common language runtime vyhledává sestavení, které odpovídá požadavku sestavení před použitím informací o kódu v konfiguračním souboru do globální mezipaměti sestavení.  
  
 Všimněte si, že jsou scénáře, kdy explicitně nechcete instalace sestavení do globální mezipaměti sestavení. Pokud umístíte jednoho sestavení, které tvoří aplikaci do globální mezipaměti sestavení, můžete už replikovat nebo nainstalujte aplikaci pomocí příkazu XCOPY zkopírovat adresář aplikace. V takovém případě musíte také přesunout sestavení do globální mezipaměti sestavení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Instalace sestavení do globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 Popisuje způsoby instalace sestavení do globální mezipaměti sestavení.  
  
 [Postupy: Zobrazení obsahu globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 Vysvětluje způsob používání [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) k zobrazení obsahu globální mezipaměti sestavení.  
  
 [Postupy: Odebrání sestavení z globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 Vysvětluje způsob používání [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) odebrání sestavení z globální mezipaměti sestavení.  
  
 [Používání obsluhovaných komponent s globální pamětí sestavení](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 Vysvětluje, proč obsluhované komponenty (spravované komponenty COM +.) umístit do globální mezipaměti sestavení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 Poskytuje přehled o vytváření sestavení.  
  
 [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)  
 Popisuje globální mezipaměti sestavení.  
  
 [Postupy: Zobrazení obsahu sestavení](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Vysvětluje způsob používání [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) k zobrazení informací Microsoft intermediate language (MSIL) v sestavení.  
  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Popisuje, jak modul common language runtime vyhledá a načte sestavení, které tvoří vaši aplikaci.  
  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Popisuje sestavení, stavební bloky spravovaných aplikací.
