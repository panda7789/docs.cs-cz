---
title: Sledování a trasování pracovních postupů
description: Sledování pracovního postupu Windows je funkce .NET Framework 4.6.1, která poskytuje sledovací infrastrukturu pro sledování provádění instance pracovního postupu.
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: f88ff68a361bf3882d75bc2d5fb21903fd283a4d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421290"
---
# <a name="workflow-tracking-and-tracing"></a>Sledování a trasování pracovních postupů
Sledování pracovního postupu Windows je [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] funkce navržená tak, aby poskytovala přehled o spuštění pracovního postupu. Poskytuje sledovací infrastrukturu pro sledování provádění instance pracovního postupu. Infrastruktura sledování WF transparentně nahrává pracovní postup k vygenerování záznamů odrážejících klíčové události během provádění. Tato funkce je ve výchozím nastavení k dispozici pro libovolný [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovní postup. U pracovního postupu není nutné provádět žádné změny, aby [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] mohlo probíhat sledování. Je jen věcí k rozhodnutí o tom, kolik dat sledování chcete získat. Když se spustí nebo dokončí instance pracovního postupu, vygenerují se záznamy sledování zpracování. Sledování může také extrahovat data relevantní pro firmy přidružená k proměnným pracovního postupu. Například pokud pracovní postup představuje systém zpracování objednávky, ID objednávky lze extrahovat spolu s <xref:System.Activities.Tracking.TrackingRecord> objektem. Obecně platí, že povolení sledování WF usnadňuje použití dat diagnostiky nebo obchodní analýzy z provádění pracovního postupu.  
  
 Tyto součásti sledování jsou ekvivalentní ke službě sledování v WinFX. V systému se [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] vylepšil výkon a zjednodušil se programovací model pro funkci sledování WF. Modul runtime sledování sleduje instanci pracovního postupu k vygenerování událostí souvisejících s životním cyklem pracovního postupu, aktivitami pracovního postupu a vlastními událostmi.  
  
 Windows Server App Fabric také umožňuje monitorovat spouštění služeb WCF a pracovních postupů. Další informace najdete v tématu monitorování a monitorování aplikací [Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10)) [s Windows serverem AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10)) .  
  
 Chcete-li vyřešit potíže s modulem runtime pracovního postupu, můžete zapnout trasování diagnostického pracovního postupu. Další informace najdete v tématu [trasování pracovního postupu](workflow-tracing.md).  
  
 Pro pochopení programovacího modelu jsou v tomto tématu popsány primární komponenty sledovací infrastruktury:  
  
- <xref:System.Activities.Tracking.TrackingRecord>objekty emitované z modulu runtime pracovního postupu. Další informace najdete v tématu [sledování záznamů](tracking-records.md).  
  
- <xref:System.Activities.Tracking.TrackingParticipant>objekty se přihlásí k odběru <xref:System.Activities.Tracking.TrackingRecord> objektů. Sledování účastníci obsahují logiku pro zpracování datové části z <xref:System.Activities.Tracking.TrackingRecord> objektů (například mohou zvolit zápis do souboru). Další informace najdete v tématu [Sledování účastníků](tracking-participants.md).  
  
- <xref:System.Activities.Tracking.TrackingProfile>objekty filtrují záznamy sledování, které byly vygenerovány z instance pracovního postupu. Další informace najdete v tématu [sledování profilů](tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>Infrastruktura sledování pracovního postupu  
 Infrastruktura sledování pracovního postupu následuje paradigma publikování a odběru. Instance pracovního postupu je Vydavatel záznamů sledování, zatímco předplatitelé záznamů sledování jsou registrováni jako rozšíření pracovního postupu. Tato rozšíření, která se přihlásí k odběru <xref:System.Activities.Tracking.TrackingRecord> objektů, se nazývají sledování účastníků. Sledování účastníků je body rozšiřitelnosti, které přistupují k <xref:System.Activities.Tracking.TrackingRecord> objektům a zpracovávají je jakýmkoli způsobem, který je zapisuje. Sledovací infrastruktura umožňuje použití filtru na odchozích záznamech sledování, aby účastník mohl přihlásit k odběru podmnožiny záznamů. Tento mechanismus filtrování je možné provést prostřednictvím souboru sledovacího profilu.  
  
 Na následujícím obrázku je zobrazený pohled na nejvyšší úroveň sledovací infrastruktury:  
  
 ![Snímek obrazovky zobrazující infrastrukturu sledování pracovního postupu.](./media/workflow-tracking-and-tracing/workflow-tracking-infrastructure.gif "WV")  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Sledování záznamů](tracking-records.md)  
 Popisuje sledování záznamů, které modul runtime pracovního postupu generuje.  
  
 [Sledování profilů](tracking-profiles.md)  
 Popisuje, jak se používají profily sledování.  
  
 [Účastníci sledování](tracking-participants.md)  
 Popisuje, jak použít účastníka sledování v systému nebo jak vytvořit vlastní sledování účastníků.  
  
 [Konfigurace sledování pracovního postupu](configuring-tracking-for-a-workflow.md)  
 Popisuje postup konfigurace sledování pracovního postupu.  
  
 [Trasování pracovních postupů](workflow-tracing.md)  
 Popisuje dva způsoby, jak povolit trasování ladění pro pracovní postup.  
  
## <a name="see-also"></a>Viz také

- [Sledování SQL](./samples/sql-tracking.md)
