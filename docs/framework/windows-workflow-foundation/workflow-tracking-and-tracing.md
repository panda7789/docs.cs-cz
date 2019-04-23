---
title: Sledování a trasování pracovních postupů
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: dbc5c0b51024c7b88b8c6cd9a052addd74e6f7e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191026"
---
# <a name="workflow-tracking-and-tracing"></a>Sledování a trasování pracovních postupů
Sledování pracovního postupu Windows je [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] funkce poskytují přehled o provádění pracovního postupu. Poskytuje sledování infrastruktury pro sledování spuštění instance pracovního postupu. Sledování infrastruktury WF nástroje transparentně pracovního postupu pro vydávání záznamy, které odráží klíče události během provádění. Tato funkce je k dispozici ve výchozím nastavení pro všechny [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu. Nejsou potřeba k tomu žádné změny [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] pracovního postupu pro sledování na výskyt. Je jenom pár rozhodování o tom, kolik dat sledování chcete dostávat. Při spuštění instance pracovního postupu nebo dokončí zpracování sledování jsou emitovány záznamy. Sledování lze rovněž extrahovat obchodní relevantní data přidružená k proměnné pracovního postupu. Například, pokud pracovní postup představuje pořadí zpracování systému, ID objednávky může být extrahována spolu s <xref:System.Activities.Tracking.TrackingRecord> objektu. Obecně platí povolení WF sledování zajišťuje diagnostiky nebo obchodní data analytics přistupovat z pracovního postupu provádění.  
  
 Tyto sledování součásti jsou ekvivalentní službě sledování v [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]. V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], vylepšili jsme výkon a jednoduché programovací model pro funkci sledování WF. Modul runtime sledování instruments instance pracovního postupu ke generování událostí souvisejících s životním cyklem pracovního postupu, aktivity pracovního postupu a vlastní události.  
  
 Windows Server App Fabric také umožňuje monitorovat spuštění služby WCF a pracovního postupu. Další informace najdete v tématu [systému Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273) a [monitorování aplikací pomocí služby Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=201287)  
  
 Řešení potíží s modulu runtime pracovního postupu, můžete zapnout trasování diagnostiky pracovního postupu. Další informace najdete v tématu [pracovního postupu trasování](workflow-tracing.md).  
  
 Informace o tom programovací model, primární součásti sledování infrastruktury jsou popsané v tomto tématu:  
  
-   <xref:System.Activities.Tracking.TrackingRecord> objekty, protože ho z modulu runtime pracovního postupu. Další informace najdete v tématu [sledování záznamů](tracking-records.md).  
  
-   <xref:System.Activities.Tracking.TrackingParticipant> přihlášení k odběru objekty <xref:System.Activities.Tracking.TrackingRecord> objekty. Sledování účastníci obsahují logiku ke zpracování datové části ze <xref:System.Activities.Tracking.TrackingRecord> objektů (například jejich může rozhodnout pro zápis do souboru). Další informace najdete v tématu [sledování účastníci](tracking-participants.md).  
  
-   <xref:System.Activities.Tracking.TrackingProfile> objekty filtrování záznamů sledování vyzařováno instance pracovního postupu. Další informace najdete v tématu [sledování profilů](tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>Pracovní postup sledování infrastruktury  
 Pracovní postup sledování infrastruktury následuje paradigma se publikování a odběr. Instance pracovního postupu je vydavatelem sledování záznamů, zatímco předplatitele sledování záznamů, které jsou registrovány jako rozšíření do pracovního postupu. Tato rozšíření by pro přihlášení k odběru <xref:System.Activities.Tracking.TrackingRecord> objekty jsou volány sledování účastníci. Sledování účastníci jsou body rozšiřitelnosti, které přistupují k <xref:System.Activities.Tracking.TrackingRecord> objektů a jejich zpracování libovolné způsobem jsou zapsány Uděláte to tak. Sledování infrastruktury umožňuje aplikaci filtru na odchozí záznamy sledování účastníka přihlásit k podmnožinu záznamů odběru povolit. Tento mechanismus filtrování se provádí prostřednictvím sleduje soubor profilu.  
  
 Zobrazení nejvyšší úrovně sledování infrastruktury můžete vidět na následujícím obrázku:  
  
 ![Snímek obrazovky zobrazující pracovní postup sledování infrastruktury. ](./media/workflow-tracking-and-tracing/workflow-tracking-infrastructure.gif "WV")  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Sledování záznamů](tracking-records.md)  
 Popisuje sledování záznamů, které generuje modul runtime pracovního postupu.  
  
 [Sledování profilů](tracking-profiles.md)  
 Tento článek popisuje, jak se používají profilů sledování.  
  
 [Účastníci sledování](tracking-participants.md)  
 Popisuje způsob použití poskytovaných systémem sledování účastník nebo vytvořit vlastní sledování účastníci.  
  
 [Konfigurace sledování pracovního postupu](configuring-tracking-for-a-workflow.md)  
 Popisuje postup konfigurace sledování pracovního postupu.  
  
 [Trasování pracovních postupů](workflow-tracing.md)  
 Popisuje dva způsoby, jak povolit trasování ladění pracovního postupu.  
  
## <a name="see-also"></a>Viz také:

- [Sledování SQL](./samples/sql-tracking.md)
