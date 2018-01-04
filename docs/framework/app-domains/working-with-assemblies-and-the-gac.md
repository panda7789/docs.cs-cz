---
title: "Práce se sestaveními a s globální pamětí sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f1ee4855745573a4b73b409279d70906191bfd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a>Práce se sestaveními a s globální pamětí sestavení
Pokud máte v úmyslu sdílet sestavení mezi více aplikacemi, můžete ji nainstalovat do globální mezipaměti sestavení. Každý počítač, kde je nainstalován modul common language runtime má tato mezipaměť strojový kód. Globální mezipaměti sestavení uchovává sestavení konkrétně určená ke sdílení více aplikacemi v počítači. Sestavení musí mít silným názvem být nainstalovaný v globální mezipaměti sestavení.  
  
> [!NOTE]
>  Sestavení, které jsou umístěny v globální mezipaměti sestavení musí mít stejný název sestavení a název souboru (bez zahrnutí příponu názvu souboru). Sestavení s názvem sestavení myAssembly musí mít například název souboru myAssembly.exe nebo myAssembly.dll.  
  
 Sestavení by měly sdílet pomocí jejich instalace do globální mezipaměti sestavení pouze v případě potřeby. V rámci obecných pokynů udržujte sestavení závislosti privátním a vyhledání sestavení v adresáři aplikace, pokud sdílení sestavení není explicitně nutné. Kromě toho nemáte instalace sestavení do globální mezipaměti sestavení do zpřístupněte je COM spolupráce nebo nespravovaného kódu.  
  
 Tady je několik důvodů, proč můžete chtít instalace sestavení do globální mezipaměti sestavení:  
  
-   Sdílené umístění.  
  
     Sestavení, která má být používána aplikace může být uvedena v globální mezipaměti sestavení. Například pokud všechny aplikace by měly používat sestavení v globální mezipaměti sestavení, prohlášení o zásadách verze lze přidat do souboru Machine.config, který přesměruje odkazy na sestavení.  
  
-   Soubor zabezpečení.  
  
     Správci často chrání kořenovou složku pomocí seznamu řízení přístupu (ACL) k řízení zápisu a provést přístup. Protože globální mezipaměti sestavení je nainstalována v kořenové složce systému, dědí řízení přístupu tohoto adresáře. Doporučuje se, že mohou pouze uživatelé s oprávněním správce k odstranění souborů z globální mezipaměti sestavení.  
  
-   Správa verzí vedle sebe.  
  
     Více kopií sestavení se stejným názvem, ale s jinou verzi informace je možné udržovat v globální mezipaměti sestavení.  
  
-   Další hledání umístění.  
  
     Modul CLR ověří globální mezipaměti sestavení pro sestavení, které odpovídají požadavku sestavení před použitím informací o kódu v konfiguračním souboru.  
  
 Všimněte si, že jsou scénáře, kde explicitně nechcete instalovat sestavení do globální mezipaměti sestavení. Pokud jeden z těchto sestavení, které tvoří aplikaci do globální mezipaměti sestavení, můžete už replikovat nebo nainstalovat aplikaci pomocí příkazu XCOPY pro kopírování adresář aplikace. V takovém případě musíte také přesunout sestavení do globální mezipaměti sestavení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Instalace sestavení do globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 Popisuje způsoby instalace sestavení do globální mezipaměti sestavení.  
  
 [Postupy: Zobrazení obsahu globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 Vysvětluje, jak používat [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) zobrazení obsahu globální mezipaměti sestavení.  
  
 [Postupy: Odebrání sestavení z globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 Vysvětluje, jak používat [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pro odebrání sestavení z globální mezipaměti sestavení.  
  
 [Používání obsluhovaných komponent s globální pamětí sestavení](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 Vysvětluje, proč obsluhované komponenty (spravované komponenty modelu COM +) musí být umístěny v globální mezipaměti sestavení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 Poskytuje přehled vytváření sestavení.  
  
 [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)  
 Popisuje globální mezipaměti sestavení.  
  
 [Postupy: Zobrazení obsahu sestavení](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Vysvětluje, jak používat [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pro zobrazení informací (MSIL intermediate language) Microsoft v sestavení.  
  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Popisuje, jak modul common language runtime vyhledá a načte sestavení, které tvoří vaši aplikaci.  
  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Popisuje sestavení, stavební bloky spravovaných aplikací.
