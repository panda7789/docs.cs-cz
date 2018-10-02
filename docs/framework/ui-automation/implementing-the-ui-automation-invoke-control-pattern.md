---
title: Implementace vzoru ovládacích prvků vyvolání pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: f6afb850b16493bab79dd368ba1ff126305f96aa
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033516"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>Implementace vzoru ovládacích prvků vyvolání pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IInvokeProvider>, včetně informací o události a vlastnosti. Odkazy na další odkazy jsou uvedeny na konci tohoto tématu.  
  
 <xref:System.Windows.Automation.InvokePattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které Udržovat stav při aktivaci ale spíše zahájit nebo jednoznačnou, kompletní jednu akci. Ovládací prvky, které udržuje stav, jako je například zaškrtávací políčka a přepínačů, musíte místo toho implementovat <xref:System.Windows.Automation.Provider.IToggleProvider> a <xref:System.Windows.Automation.Provider.ISelectionItemProvider> v uvedeném pořadí. Příklady ovládacích prvků, které implementují vzor Invoke ovládacích prvků naleznete v tématu [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Pokud implementace vzoru ovládacích prvků Invoke, mějte na paměti následující pokyny a konvence:  
  
-   Implementace ovládacích prvků <xref:System.Windows.Automation.Provider.IInvokeProvider> Pokud stejné chování se nevystaví prostřednictvím jiného poskytovatele řízení vzor. Například pokud <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metoda na ovládací prvek provádí stejnou akci, jako <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> nebo <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> metody by neměla implementovat ovládací prvek <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
-   Vyvolání ovládacího prvku se obvykle provádí kliknutím nebo poklepáním nebo stisknutím klávesy ENTER, předdefinované klávesové zkratky nebo alternativní kombinaci kláves.  
  
-   <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> je aktivována na ovládací prvek, který se aktivoval (jako odpověď na ovládací prvek jeho přidružené akce). Pokud je to možné by měl událost vyvolána po ovládací prvek dokončil akci a vrátí bez blokování. Událost vyvolaná by měla být zvýšena před obsluze žádosti Invoke v následujících scénářích:  
  
    -   Není možné nebo praktické počkat, až se akce dokončí.  
  
    -   Tato akce vyžaduje zásah uživatele.  
  
    -   Tato akce je časově náročné a způsobí, že volajícího klienta a blokovat významné množství času.  
  
-   Pokud volání ovládacího prvku má významné vedlejší účinky, tyto vedlejší účinky by měly být vystaveny prostřednictvím <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> vlastnost. Například i když <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> není přidružen k výběru, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> může způsobit, že jiný ovládací prvek má být vybrán.  
  
-   Při najetí myší (nebo myší nad) účinky obecně nepředstavují vyvolaná událost. Však podporovat ovládací prvky, které provádějí akce (na rozdíl od příčina vizuální efekt). v závislosti na stavu při najetí myší <xref:System.Windows.Automation.InvokePattern> – vzor ovládacích prvků.  
  
> [!NOTE]
>  Tato implementace se považuje za problém usnadnění přístupu, pokud ovládací prvek lze vyvolat pouze v důsledku vedlejší účinek týkající se myši.  
  
-   Vyvolání ovládacího prvku se liší od výběru nějaké položky. Ale v závislosti na ovládacím prvku vyvolání může způsobit, že položka, která má být vybrána jako vedlejší efekt. Například volání [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] položky seznamu dokumentů ve složce Dokumenty vybere položka i otevře dokument.  
  
-   Element může zmizí z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu ihned po vyvolání. Žádá se informace z elementu poskytované události zpětného volání může selhat v důsledku. Předběžné načítání informací uložených v mezipaměti je doporučené řešení.  
  
-   Ovládací prvky můžete implementovat několik vzorů ovládacích prvků. Například barva výplně ovládacího prvku na [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] nástrojů implementuje oba <xref:System.Windows.Automation.InvokePattern> a <xref:System.Windows.Automation.ExpandCollapsePattern> řídit vzory. <xref:System.Windows.Automation.ExpandCollapsePattern> zpřístupňuje v nabídce a <xref:System.Windows.Automation.InvokePattern> vyplní aktivního výběru zvolený barvou.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iinvokeprovider"></a>Požadované členy pro IInvokeProvider  
 Následující vlastnosti a metody, které jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|– metoda|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> je asynchronní volání a musí vrátit okamžitě bez blokování.<br /><br /> Toto chování je obzvláště důležité pro ovládací prvky, které přímo nebo nepřímo, spusťte modální dialogové okno při vyvolání. Jakékoli automatizace uživatelského rozhraní klienta, který zahájené události zůstane blokované, dokud není zavřena modální dialogové okno.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Poskytovatelé musí vyvolání následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Pokud je ovládací prvek není povoleno.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
