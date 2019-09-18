---
title: Implementace vzoru ovládacích prvků vyvolání pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
ms.openlocfilehash: e9815e4c2c0740f213632681200e48c8e4786657
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043396"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>Implementace vzoru ovládacích prvků vyvolání pro automatizaci uživatelského rozhraní

> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.

Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IInvokeProvider>implementaci, včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.

Vzor <xref:System.Windows.Automation.InvokePattern> ovládacího prvku se používá k podpoře ovládacích prvků, které neudržují stav při aktivaci, ale spíše iniciuje nebo provádí jednu nejednoznačnou akci. Ovládací prvky, které udržují stav, jako jsou zaškrtávací políčka a přepínače, musí místo <xref:System.Windows.Automation.Provider.IToggleProvider> toho <xref:System.Windows.Automation.Provider.ISelectionItemProvider> implementovat a v uvedeném pořadí. Příklady ovládacích prvků, které implementují vzor ovládacího prvku Invoke, najdete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace

Při implementaci vzoru ovládacího prvku Invoke si všimněte následujících pokynů a konvencí:

- Ovládací prvky <xref:System.Windows.Automation.Provider.IInvokeProvider> implementují, pokud se stejné chování nezveřejňuje prostřednictvím jiného poskytovatele vzoru prvku. Například pokud <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metoda na ovládacím prvku provede stejnou akci <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> jako metoda nebo <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> , ovládací prvek by neměl být implementován <xref:System.Windows.Automation.Provider.IInvokeProvider>.

- Vyvolání ovládacího prvku je obecně prováděno kliknutím nebo poklikáním nebo stisknutím klávesy ENTER, předdefinovanou klávesovou zkratkou nebo jinou kombinací kláves.

- <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>je vyvolána na ovládacím prvku, který byl aktivován (jako odpověď na ovládací prvek, který provádí přidruženou akci). Pokud je to možné, událost by měla být vyvolána poté, co ovládací prvek dokončí akci a vrátí se bez blokování. Vyvolaná událost by měla být vyvolána před obsluhou žádosti o vyvolání v následujících scénářích:

  - Není možné nebo je praktické počkat na dokončení akce.

  - Akce vyžaduje zásah uživatele.

  - Akce je časově náročná a způsobí, že volající klient bude po významné době blokovat.

- Pokud vyvolání ovládacího prvku má významné vedlejší účinky, tyto vedlejší účinky by měly být vystaveny prostřednictvím <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> vlastnosti. Například, i když <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> není přidružen k výběru, může způsobit, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> že se vybere jiný ovládací prvek.

- Efekty najetí myší (nebo myš) obecně nepředstavují vyvolanou událost. Nicméně ovládací prvky, které provádějí akci (na rozdíl od toho, že způsobují vizuální efekt), by měly podporovat <xref:System.Windows.Automation.InvokePattern> vzor ovládacího prvku.

> [!NOTE]
> Tato implementace je považována za problém s přístupností, pokud lze ovládací prvek vyvolat pouze v důsledku vedlejšího efektu souvisejícího s myší.

- Vyvolání ovládacího prvku se liší od výběru položky. V závislosti na ovládacím prvku ale volání může způsobit, že se položka vybere jako vedlejší efekt. Například vyvolání [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] položky seznamu dokumentů ve složce Dokumenty vybere položku a otevře dokument.

- Element může z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu zmizet ihned po jeho vyvolání. Žádost o informace z prvku poskytnutého zpětným voláním události může být způsobena selháním. Doporučené řešení je předběžné načítání informací uložených v mezipaměti.

- Ovládací prvky mohou implementovat více vzorů ovládacích prvků. Například ovládací prvek Barva výplně na [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] panelu nástrojů implementuje <xref:System.Windows.Automation.InvokePattern> vzory i <xref:System.Windows.Automation.ExpandCollapsePattern> ovládací prvky. <xref:System.Windows.Automation.ExpandCollapsePattern>zpřístupní nabídku a <xref:System.Windows.Automation.InvokePattern> vyplní aktivní výběr zvolenou barvou.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iinvokeprovider"></a>Vyžadovaná členové pro IInvokeProvider

Pro implementaci <xref:System.Windows.Automation.Provider.IInvokeProvider>jsou vyžadovány následující vlastnosti a metody.

|Vyžadovaná členové|Typ člena|Poznámky|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|– metoda|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>je asynchronní volání a musí ihned vracet bez blokování.<br /><br /> Toto chování je zvláště důležité pro ovládací prvky, které přímo nebo nepřímo spouštějí modální dialog při vyvolání. Jakýkoli klient automatizace uživatelského rozhraní, který událost vybere, zůstane blokovaný, dokud se modální dialogové okno nezavře.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Výjimky

Zprostředkovatelé musí vyvolat následující výjimky.

|Typ výjimky|Podmínka|
|--------------------|---------------|
|<xref:System.Windows.Automation.ElementNotEnabledException>|Pokud ovládací prvek není povolený.|

## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní](invoke-a-control-using-ui-automation.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
