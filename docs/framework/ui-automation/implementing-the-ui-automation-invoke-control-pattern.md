---
title: "Implementace vzoru ovládacích prvků vyvolání pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
caps.latest.revision: "31"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1d40bc94887df604577c025181ae7f5f2776cdc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>Implementace vzoru ovládacích prvků vyvolání pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IInvokeProvider>, včetně informací o události a vlastnosti. Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.InvokePattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které uchování stavu, pokud je aktivován ale spíše inicializovat nebo provedení jednoho, jednoznačným akce. Ovládací prvky, které udržují stavu, například zaškrtávací políčka a přepínače, místo toho musí implementovat <xref:System.Windows.Automation.Provider.IToggleProvider> a <xref:System.Windows.Automation.Provider.ISelectionItemProvider> v uvedeném pořadí. Příklady ovládacích prvků, které implementují vzor Invoke ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Při implementaci vzoru Invoke ovládacích prvků, poznamenejte si následující pokyny a konvence:  
  
-   Ovládací prvky implementovat <xref:System.Windows.Automation.Provider.IInvokeProvider> Pokud stejné chování nebude vystavena prostřednictvím jiného poskytovatele vzor ovládacího prvku. Například pokud <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metoda v ovládacím prvku provede stejnou akci, jako <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> nebo <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> metody ovládacího prvku by neměly implementovat <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
-   Vyvolání ovládacího prvku se obvykle provádí klepnutím nebo dvakrát kliknete na soubor nebo stisknutím ENTER, předdefinované klávesové zkratky nebo některé alternativní kombinace kláves.  
  
-   <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>je vyvolána na ovládací prvek, který byl aktivován (jako odpověď do ovládacího prvku jeho přidružené akce). Pokud je to možné by měl být událost vyvolána po dokončil akci a vrátí bez blokování ovládacího prvku. Událost Invoked by měl být vyvolána před obsluhy Invoke žádosti v následujících scénářích:  
  
    -   Není možné ani praktické počkejte na dokončení akce.  
  
    -   Akce vyžaduje interakci uživatele.  
  
    -   Akce je časově náročná a způsobí, že volajícího klienta blokovat pro významné množství času.  
  
-   Pokud vyvolání ovládacího prvku má významné vedlejší účinky, by měly být tyto vedlejší účinky vystaveny prostřednictvím <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> vlastnost. Například i když <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> není přidružen k výběru, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> může způsobit, že jiný řízení jako vybrané.  
  
-   Při přechodu myší (nebo myší nad) důsledky obecně nepředstavují Invoked událost. Však musí podporovat ovládacích prvků, které provedení akce (na rozdíl od příčina vizuální efekt) na základě stavu přechodu <xref:System.Windows.Automation.InvokePattern> – vzor ovládacích prvků.  
  
> [!NOTE]
>  Tato implementace je považován za usnadnění problém, pokud ovládacího prvku nelze vyvolat jenom v důsledku vedlejším účinkem související myši.  
  
-   Vyvolání ovládacího prvku se liší od výběrem položky. V závislosti na ovládací prvek, však může ho vyvolání položka, která má jako vybrané jako vedlejším účinkem způsobit. Například volání [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] položky seznamu dokumentu ve složce Dokumenty vybere položka i otevře dokument.  
  
-   Element může zmizet z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu okamžitě po vyvolání. Vyžadování informací o z zadaný element zpětného volání události pravděpodobně v důsledku nezdaří. Předběžné načítání informace uložené v mezipaměti je doporučená řešení.  
  
-   Ovládací prvky můžete implementovat několik vzorů ovládacích prvků. Například ovládacího prvku Barva výplně na [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] nástrojů implementuje i <xref:System.Windows.Automation.InvokePattern> a <xref:System.Windows.Automation.ExpandCollapsePattern> řízení vzory. <xref:System.Windows.Automation.ExpandCollapsePattern>zpřístupní v nabídce a <xref:System.Windows.Automation.InvokePattern> doplní aktivní výběr zvolené barvou.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iinvokeprovider"></a>Požadované členy pro IInvokeProvider  
 Následující vlastnosti a metody jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|– metoda|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>je asynchronní volání a musí vracet okamžitě bez blokování.<br /><br /> Toto chování je obzvláště důležité pro ovládací prvky, které přímo nebo nepřímo, spusťte modální dialogové okno při vyvolání. Libovolného automatizace uživatelského rozhraní klienta, který zahájené událost zůstane blokovaný, dokud modální dialogové okno je uzavřený.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Pokud ovládací prvek není povolena.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
