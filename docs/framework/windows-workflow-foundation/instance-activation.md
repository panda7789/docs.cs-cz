---
title: Instance aktivace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d33e809a0db0b812cf7311d7b5686d9125e80976
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="instance-activation"></a>Instance aktivace
Ukládání Instance pracovního postupu SQL spustí vnitřní úloh, která pravidelně probudí a zjišťuje instance pracovního postupu spustitelného nebo activatable v databázi trvalost. Pokud najde instanci spustitelného pracovního postupu, upozorní hostitele pracovního postupu, který je schopen aktivace instance. Pokud instance úložiště najde instance activatable pracovního postupu, upozorní obecné hostitele, který aktivuje hostitele pracovního postupu, který pak spustí instanci pracovního postupu. Následující části v tomto tématu popisují proces aktivace instance podrobně.  
  
##  <a name="RunnableSection"></a>Zjišťování a aktivace instance spustitelného pracovních postupů  
 Ukládání Instance pracovního postupu SQL považuje instance pracovního postupu *spustitelného* Pokud instance není v pozastaveném stavu nebo stavu dokončení a splňuje následující podmínky:  
  
-   Instance je odemčený a má čekající časovač s vypršenou platností.  
  
-   Instance má na zámek vypršela platnost.  
  
-   Instance je odemčený a její stav je **zpracování**.  
  
 Vyvolá ukládání Instance pracovního postupu SQL <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> Pokud najde spustitelného instance. Poté SqlWorkflowInstanceStore zastaví monitorování až <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> je jednou volána v úložišti.  
  
 Hostitele pracovního postupu, který má přihlášený(á) k odběru <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> a provede podporující načítání instance <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> proti úložiště instance k načtení instance do paměti. Hostitel pracovního postupu se považuje za schopná načítání instance pracovního postupu, pokud vlastnost metadat hostitele a instance **WorkflowServiceType** nastaví na stejnou hodnotu.  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>Zjišťování a aktivace instancí Activatable pracovních postupů  
 Instance pracovního postupu se považuje za *activatable* Pokud instance je spustitelného a není žádné hostitele pracovního postupu, který je schopen načítání instance běží na počítači. Pro danou definici instanci spustitelného pracovního postupu v tématu zjištění a aktivace spustitelného instance pracovního postupu výše.  
  
 Vyvolá ukládání Instance pracovního postupu SQL <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> Pokud najde instance pracovního postupu activatable v databázi. Poté SqlWorkflowInstanceStore zastaví monitorování až <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> je jednou volána v úložišti.  
  
 Při obecné hostitele, který má přihlášený(á) k odběru <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> přijímá události, se provede <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> proti úložiště instance k získání aktivační parametry, které jsou potřebné pro vytvoření hostitele pracovního postupu. Obecné hostitel používá tyto aktivační parametry pro vytvoření hostitele pracovního postupu, který naopak načte a spustí instanci spustitelného služby.  
  
## <a name="generic-hosts"></a>Obecné hostitele  
 Obecné hostitel je hostitele, který má hodnotu vlastnosti metadat **WorkflowServiceType** pro obecné hostitele je nastavena na **WorkflowServiceType.Any** k označení, že je zpracovat libovolný typ pracovního postupu. Obecné hostitele má parametr XName s názvem **ActivationType**.  
  
 V současné době podporuje ukládání Instance pracovního postupu SQL obecné hostitele s hodnotou parametru ActivationType nastavena na **WAS**. Pokud ActivationType není nastaven na WAS, vyvolá ukládání Instance pracovního postupu SQL <xref:System.Runtime.DurableInstancing.InstancePersistenceException>. Služba správy pracovního postupu, který se dodává s [!INCLUDE[dublin](../../../includes/dublin-md.md)] je obecný hostitele, který má typ aktivace nastavený na **WAS**.  
  
 Aktivace WAS obecné hostitele vyžaduje sadu parametrů aktivace odvození adresa koncového bodu, na které je možné aktivovat nové hostitele. Parametry aktivace pro aktivaci WAS jsou název lokality, cesta k aplikaci relativně k webu a cestu ke službě vzhledem k aplikaci. Ukládání Instance pracovního postupu SQL ukládá tyto parametry aktivace během provádění <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>.  
  
## <a name="runnable-instances-detection-period"></a>Období detekce spustitelného instancí  
 **Spustitelného období zjišťování instancí** vlastnost úložiště Instance pracovního postupu SQL určuje časové období, po jejímž uplynutí ukládání Instance pracovního postupu SQL spustí úlohu detekce ke zjištění všech spustitelného nebo activatable pracovního postupu instance v databázi trvalost předchozího cyklu zjišťování. V tématu [spustitelného období zjišťování instancí](../../../docs/framework/windows-workflow-foundation/runnable-instances-detection-period.md) další podrobnosti o této vlastnosti.
