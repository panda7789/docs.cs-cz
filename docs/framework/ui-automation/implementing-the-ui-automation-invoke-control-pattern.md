---
title: Implementace vzoru ovládacích prvků vyvolání pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
ms.openlocfilehash: 616bbab4d659cf00b1f730492e73ad6b847e3926
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457998"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>Implementace vzoru ovládacích prvků vyvolání pro automatizaci uživatelského rozhraní

> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).

This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IInvokeProvider>, including information about events and properties. Links to additional references are listed at the end of the topic.

The <xref:System.Windows.Automation.InvokePattern> control pattern is used to support controls that do not maintain state when activated but rather initiate or perform a single, unambiguous action. Controls that do maintain state, such as check boxes and radio buttons, must instead implement <xref:System.Windows.Automation.Provider.IToggleProvider> and <xref:System.Windows.Automation.Provider.ISelectionItemProvider> respectively. For examples of controls that implement the Invoke control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions

When implementing the Invoke control pattern, note the following guidelines and conventions:

- Controls implement <xref:System.Windows.Automation.Provider.IInvokeProvider> if the same behavior is not exposed through another control pattern provider. For example, if the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method on a control performs the same action as the <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> method, the control should not implement <xref:System.Windows.Automation.Provider.IInvokeProvider>.

- Invoking a control is generally performed by clicking or double-clicking or pressing ENTER, a predefined keyboard shortcut, or some alternate combination of keystrokes.

- <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> is raised on a control that has been activated (as a response to a control carrying out its associated action). If possible, the event should be raised after the control has completed the action and returned without blocking. The Invoked event should be raised before servicing the Invoke request in the following scenarios:

  - It is not possible or practical to wait until the action is complete.

  - The action requires user interaction.

  - The action is time-consuming and will cause the calling client to block for a significant amount of time.

- Pokud vyvolání ovládacího prvku má významné vedlejší účinky, tyto vedlejší účinky by měly být zpřístupněny prostřednictvím vlastnosti <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>. Například, i když <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> není přidružená k výběru, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> může způsobit, že se vybere jiný ovládací prvek.

- Efekty najetí myší (nebo myš) obecně nepředstavují vyvolanou událost. Nicméně ovládací prvky, které provádějí akci (na rozdíl od toho, že způsobují vizuální efekt), by měly podporovat vzor ovládacího prvku <xref:System.Windows.Automation.InvokePattern>.

> [!NOTE]
> Tato implementace je považována za problém s přístupností, pokud lze ovládací prvek vyvolat pouze v důsledku vedlejšího efektu souvisejícího s myší.

- Vyvolání ovládacího prvku se liší od výběru položky. V závislosti na ovládacím prvku ale volání může způsobit, že se položka vybere jako vedlejší efekt. Například vyvolání položky v seznamu dokumentů aplikace Microsoft Word ve složce Dokumenty vybere položku a otevře dokument.

- Element může zmizet z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu hned po jeho vyvolání. Žádost o informace z prvku poskytnutého zpětným voláním události může být způsobena selháním. Doporučené řešení je předběžné načítání informací uložených v mezipaměti.

- Ovládací prvky mohou implementovat více vzorů ovládacích prvků. Například ovládací prvek Barva výplně na panelu nástrojů aplikace Microsoft Excel implementuje jak <xref:System.Windows.Automation.InvokePattern>, tak <xref:System.Windows.Automation.ExpandCollapsePattern> vzory ovládacích prvků. <xref:System.Windows.Automation.ExpandCollapsePattern> zpřístupňuje nabídku a <xref:System.Windows.Automation.InvokePattern> vyplní aktivní výběr zvolenou barvou.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iinvokeprovider"></a>Vyžadovaná členové pro IInvokeProvider

Pro implementaci <xref:System.Windows.Automation.Provider.IInvokeProvider>jsou vyžadovány následující vlastnosti a metody.

|Vyžadovaná členové|Typ člena|Poznámky|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|– metoda|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> je asynchronní volání a musí ihned vracet bez blokování.<br /><br /> Toto chování je zvláště důležité pro ovládací prvky, které přímo nebo nepřímo spouštějí modální dialog při vyvolání. Jakýkoli klient automatizace uživatelského rozhraní, který událost vybere, zůstane blokovaný, dokud se modální dialogové okno nezavře.|

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
