---
title: Pracovní postup sledování a trasování
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: 8490299e995a469860f660a50a69915d5ddc4940
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731612"
---
# <a name="workflow-tracking-and-tracing"></a>Pracovní postup sledování a trasování
Sledování pracovního postupu Windows je [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] funkce poskytují přehled o provádění pracovního postupu. Poskytuje sledování infrastruktury pro sledování spuštění instance pracovního postupu. Sledování infrastruktury WF nástroje transparentně pracovního postupu pro vydávání záznamy, které odráží klíče události během provádění. Tato funkce je k dispozici ve výchozím nastavení pro všechny [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu. Nejsou potřeba k tomu žádné změny [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] pracovního postupu pro sledování na výskyt. Je jenom pár rozhodování o tom, kolik dat sledování chcete dostávat. Při spuštění instance pracovního postupu nebo dokončí zpracování sledování jsou emitovány záznamy. Sledování lze rovněž extrahovat obchodní relevantní data přidružená k proměnné pracovního postupu. Například, pokud pracovní postup představuje pořadí zpracování systému, ID objednávky může být extrahována spolu s <xref:System.Activities.Tracking.TrackingRecord> objektu. Obecně platí povolení WF sledování zajišťuje diagnostiky nebo obchodní data analytics přistupovat z pracovního postupu provádění.  
  
 Tyto sledování součásti jsou ekvivalentní službě sledování v [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]. V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], vylepšili jsme výkon a jednoduché programovací model pro funkci sledování WF. Modul runtime sledování instruments instance pracovního postupu ke generování událostí souvisejících s životním cyklem pracovního postupu, aktivity pracovního postupu a vlastní události.  
  
 Windows Server App Fabric také umožňuje monitorovat spuštění služby WCF a pracovního postupu. Další informace najdete v tématu [systému Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273) a [monitorování aplikací pomocí služby Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=201287)  
  
 Řešení potíží s modulu runtime pracovního postupu, můžete zapnout trasování diagnostiky pracovního postupu. Další informace najdete v tématu [pracovního postupu trasování](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md).  
  
 Informace o tom programovací model, primární součásti sledování infrastruktury jsou popsané v tomto tématu:  
  
-   <xref:System.Activities.Tracking.TrackingRecord> objekty, protože ho z modulu runtime pracovního postupu. Další informace najdete v tématu [sledování záznamů](../../../docs/framework/windows-workflow-foundation/tracking-records.md).  
  
-   <xref:System.Activities.Tracking.TrackingParticipant> přihlášení k odběru objekty <xref:System.Activities.Tracking.TrackingRecord> objekty. Sledování účastníci obsahují logiku ke zpracování datové části ze <xref:System.Activities.Tracking.TrackingRecord> objektů (například jejich může rozhodnout pro zápis do souboru). Další informace najdete v tématu [sledování účastníci](../../../docs/framework/windows-workflow-foundation/tracking-participants.md).  
  
-   <xref:System.Activities.Tracking.TrackingProfile> objekty filtrování záznamů sledování vyzařováno instance pracovního postupu. Další informace najdete v tématu [sledování profilů](../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>Pracovní postup sledování infrastruktury  
 Pracovní postup sledování infrastruktury následuje paradigma se publikování a odběr. Instance pracovního postupu je vydavatelem sledování záznamů, zatímco předplatitele sledování záznamů, které jsou registrovány jako rozšíření do pracovního postupu. Tato rozšíření by pro přihlášení k odběru <xref:System.Activities.Tracking.TrackingRecord> objekty jsou volány sledování účastníci. Sledování účastníci jsou body rozšiřitelnosti, které přistupují k <xref:System.Activities.Tracking.TrackingRecord> objektů a jejich zpracování libovolné způsobem jsou zapsány Uděláte to tak. Sledování infrastruktury umožňuje aplikaci filtru na odchozí záznamy sledování účastníka přihlásit k podmnožinu záznamů odběru povolit. Tento mechanismus filtrování se provádí prostřednictvím sleduje soubor profilu.  
  
 Vyšší úroveň tohoto sledování infrastruktury je znázorněno na následujícím obrázku.  
  
 ![Pracovní postup sledování infrastruktury](../../../docs/framework/windows-workflow-foundation/media/wv.gif "WV")  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Sledování záznamů](../../../docs/framework/windows-workflow-foundation/tracking-records.md)  
 Popisuje sledování záznamů, které generuje modul runtime pracovního postupu.  
  
 [Sledování profilů](../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
 Tento článek popisuje, jak se používají profilů sledování.  
  
 [Účastníci sledování](../../../docs/framework/windows-workflow-foundation/tracking-participants.md)  
 Popisuje způsob použití poskytovaných systémem sledování účastník nebo vytvořit vlastní sledování účastníci.  
  
 [Konfigurace sledování pracovního postupu](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)  
 Popisuje postup konfigurace sledování pracovního postupu.  
  
 [Trasování pracovních postupů](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 Popisuje dva způsoby, jak povolit trasování ladění pracovního postupu.  
  
 [Určení doby trvání provádění pracovního postupu pomocí trasování](../../../docs/framework/windows-workflow-foundation/determining-workflow-execution-duration-using-tracing.md)  
 Popisuje způsob použití trasovací zprávy k určení doby trvání provádění pracovního postupu.  
  
## <a name="see-also"></a>Viz také  
 [Sledování SQL](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)
