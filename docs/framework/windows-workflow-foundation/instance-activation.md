---
title: Aktivace instance
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: 78f134ca2d78261a5f6ff9376bd9a98116315f0c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366042"
---
# <a name="instance-activation"></a>Aktivace instance
Store Instance pracovního postupu SQL spouští interní úlohy, která pravidelně probudí a instance pracovních postupů spustitelných nebo aktivovatelné zjistí databáze trvalosti. Pokud najde instance pracovního postupu spustitelný, upozorní hostitele pracovního postupu, které podporují aktivaci instance. Pokud v úložišti instancí najde instanci aktivovatelné pracovního postupu, upozorní obecný hostitele, který aktivuje hostitele pracovního postupu, která pak spustí instanci pracovního postupu. Následující části v tomto tématu popisují proces aktivace instance podrobně.  
  
## <a name="RunnableSection"></a> Zjišťování a aktivace spustitelné instance pracovního postupu  
 Store Instance pracovního postupu SQL bude považovat za instanci pracovního postupu *spustitelných* Pokud instance není v pozastaveném stavu nebo stavu dokončení a splňuje následující podmínky:  
  
-   Instance odemknut a má čekajícího časovače, kterému vypršela platnost.  
  
-   Instance má vypršela platnost zámku na něj.  
  
-   Instance je odemknutá a že má stav **zpracování**.  
  
 Vyvolá Store Instance pracovního postupu SQL <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> když najde spustitelné instanci. Potom úložiště SqlWorkflowInstanceStore zastaví monitorování až <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> se volá jednou ve storu.  
  
 Hostitele pracovního postupu, který má přihlášený(á) k odběru <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> a dokáže načítání instance, spustí <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> proti úložiště instance k načtení instance do paměti. Hostitel pracovního postupu se považuje za podporující načítání instance pracovního postupu, pokud mají vlastnosti metadat o hostiteli a instance **WorkflowServiceType** nastavena na stejnou hodnotu.  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>Zjišťování a aktivace instance aktivovatelné pracovních postupů  
 Instance pracovního postupu se považuje za *aktivovatelné* Pokud instance je spustitelný a neexistuje žádné hostitele pracovního postupu, který podporuje načítání instance běží v počítači. Definice instance spustitelných pracovního postupu naleznete v tématu zjištění a aktivace spustitelných instancí pracovního postupu výše.  
  
 Vyvolá Store Instance pracovního postupu SQL <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> při instance pracovního postupu aktivovatelné najde v databázi. Potom úložiště SqlWorkflowInstanceStore zastaví monitorování až <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> se volá jednou ve storu.  
  
 Při obecné hostitele, který má přihlášený(á) k odběru <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> přijímá události, je spuštěn <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> proti v úložišti instancí k získání aktivační parametry potřebné pro vytvoření hostitele pracovního postupu. Obecný hostitel používá tyto aktivační parametry k vytvoření hostitele pracovního postupu, která pak načte a spustí instanci spustitelných služby.  
  
## <a name="generic-hosts"></a>Obecný hostitele  
 Obecný hostitel je hostitel s hodnotou vlastnosti metadat **WorkflowServiceType** pro obecný hostitele je nastavena na **WorkflowServiceType.Any** k označení, že dokáže zpracovat jakýkoli typ pracovního postupu. Obecný hostitele má XName parametr s názvem **ActivationType**.  
  
 V současné době Store Instance pracovního postupu SQL podporuje obecné hostitele s hodnotou ActivationType parametrem nastaveným na **WAS**. Pokud ActivationType není nastaven na služba WAS, vyvolá Store Instance pracovního postupu SQL <xref:System.Runtime.DurableInstancing.InstancePersistenceException>. Služba správy pracovního postupu, který se dodává s [!INCLUDE[dublin](../../../includes/dublin-md.md)] je obecný hostitele, který má typ aktivace nastavený na **WAS**.  
  
 Pro aktivaci WAS obecný hostitel vyžaduje sadu parametrů aktivace pro odvození adresu koncového bodu, ve kterém můžete aktivovat nové hostitele. Parametry aktivace pro aktivaci WAS jsou název lokality, cesta k aplikaci vzhledem k webu a cestu ke službě vzhledem k aplikaci. Store Instance pracovního postupu SQL ukládá tyto parametry aktivace během provádění <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>.  
  
## <a name="runnable-instances-detection-period"></a>Interval detekce spustitelných instancí  
 **Období zjišťování spustitelných instancí** vlastnost Store Instance pracovního postupu SQL určuje časové období, po jejímž uplynutí Store Instance pracovního postupu SQL spustí úlohu detekce zjistit žádné spustitelné nebo aktivovatelné pracovního postupu instance databáze stálost po dokončení předchozího cyklu zjišťování. Zobrazit [období zjišťování spustitelných instancí](../../../docs/framework/windows-workflow-foundation/runnable-instances-detection-period.md) podrobné informace o této vlastnosti.
