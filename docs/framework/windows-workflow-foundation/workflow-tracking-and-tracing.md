---
title: Pracovní postup sledování a trasování
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: b9c1f300bcf765cf4f74ac8a8fcf4ce34c5bd967
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-tracking-and-tracing"></a>Pracovní postup sledování a trasování
Sledování pracovní postup systému je [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] funkce poskytují přehled o spuštění pracovního postupu. Poskytuje sledování infrastruktury ke sledování provádění instanci pracovního postupu. Sledování infrastruktury WF instruments transparentně pracovního postupu pro vydávání záznamy odrážející klíče události během provádění. Tato funkce je dostupná ve výchozím nastavení pro všechny [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu. Je potřeba provést žádné změny [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] pracovního postupu pro sledování proběhnout. Je pouze stačit rozhodnutí, jaké množství dat sledování, které chcete dostávat. Pokud instance pracovního postupu spustí nebo dokončí zpracování sledování jsou vygenerované záznamy. Sledování lze rovněž extrahovat obchodní relevantní data přidružená k proměnné pracovního postupu. Například pokud pracovní postup představuje pořadí zpracování systému, pořadí ID lze extrahovat spolu s <xref:System.Activities.Tracking.TrackingRecord> objektu. Obecně platí povolení WF sledování usnadňuje diagnostiku nebo obchodní analytická data nelze přistupovat ze spuštění pracovního postupu.  
  
 Toto sledování součásti jsou ekvivalentní službě sledování v [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]. V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], vylepšila výkon a zjednodušená programovací model pro funkci sledování WF. Modul runtime sledování instruments instanci pracovního postupu pro vydávání událostí související pracovní postup životní cyklus, aktivity pracovního postupu a vlastních událostí.  
  
 Windows Server App Fabric taky poskytuje možnost monitorovat služby WCF a pracovní postup. Další informace najdete v tématu [Windows Server App Fabric monitorování](http://go.microsoft.com/fwlink/?LinkId=201273) a [monitorování aplikací s Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201287)  
  
 Chcete-li vyřešit modulu runtime pracovního postupu, můžete zapnout trasování postupu diagnostiky. Další informace najdete v tématu [trasování pracovního postupu](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md).  
  
 Zjistit programovací model primární součásti sledování infrastruktury jsou popsané v tomto tématu:  
  
-   <xref:System.Activities.Tracking.TrackingRecord> objekty vygenerované z modulu runtime pracovního postupu. Další informace najdete v tématu [sledování záznamů](../../../docs/framework/windows-workflow-foundation/tracking-records.md).  
  
-   <xref:System.Activities.Tracking.TrackingParticipant> přihlášení k odběru objektů <xref:System.Activities.Tracking.TrackingRecord> objekty. Sledování účastníků obsahují logiku ke zpracování datové části z <xref:System.Activities.Tracking.TrackingRecord> objekty (například se může zvolit k zápisu do souboru). Další informace najdete v tématu [sledování účastníky](../../../docs/framework/windows-workflow-foundation/tracking-participants.md).  
  
-   <xref:System.Activities.Tracking.TrackingProfile> objekty filtrování záznamů sledování vygenerované z instance pracovního postupu. Další informace najdete v tématu [sledování profily](../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>Pracovní postup sledování infrastruktury  
 Sledování infrastruktury pracovního postupu následuje zlepší se publikovat a odebírat. Instance pracovního postupu je vydavatel sledování záznamů, při sledování záznamů Odběratelé, kteří jsou registrované jako rozšíření do pracovního postupu. Tato rozšíření by pro přihlášení k odběru <xref:System.Activities.Tracking.TrackingRecord> objekty se nazývají sledování účastníky. Sledování účastníků jsou body rozšiřitelnosti, která přistupují k <xref:System.Activities.Tracking.TrackingRecord> objekty a jejich zpracování v jakýmkoli způsobem jsou zapsané do učinit. Sledování infrastruktury umožňuje použití filtru v odchozí sledování záznamy, které chcete povolit účastníka k odběru podmnožinu záznamy. Tento mechanismus filtrování se provádí prostřednictvím sledování souboru profilu.  
  
 Na následujícím obrázku se zobrazuje nejvyšší úrovni zobrazení sledování infrastruktury.  
  
 ![Pracovní postup sledování infrastruktury](../../../docs/framework/windows-workflow-foundation/media/wv.gif "WV")  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Sledování záznamů](../../../docs/framework/windows-workflow-foundation/tracking-records.md)  
 Popisuje sledování záznamy, které vysílá modulu runtime pracovního postupu.  
  
 [Sledování profilů](../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
 Popisuje, jak se používají sledování profily.  
  
 [Účastníci sledování](../../../docs/framework/windows-workflow-foundation/tracking-participants.md)  
 Popisuje postup použití účastník poskytované systémem sledování nebo jak vytvořit vlastní sledování účastníky.  
  
 [Konfigurace sledování pracovního postupu](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)  
 Popisuje postup konfigurace sledování pro pracovní postup.  
  
 [Trasování pracovních postupů](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 Popisuje dva způsoby, jak povolit trasování ladění pro pracovní postup.  
  
 [Určení doby trvání provádění pracovního postupu pomocí trasování](../../../docs/framework/windows-workflow-foundation/determining-workflow-execution-duration-using-tracing.md)  
 Popisuje, jak používat zprávy trasování určete dobu trvání provádění pracovního postupu.  
  
## <a name="see-also"></a>Viz také  
 [Sledování SQL](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)
