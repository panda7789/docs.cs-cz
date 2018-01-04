---
title: "Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
caps.latest.revision: "25"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4811b3273ba829882dadffe95ff8c29fb8ee7400
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IValueProvider>, včetně informací o vlastnostech a události. Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.ValuePattern> – Vzor ovládacích prvků se používá pro podporu ovládací prvky, které mají vnitřní hodnotu není pokrývání uzlů rozsah a který může být reprezentován jako řetězec. Tento řetězec lze upravovat, v závislosti na ovládací prvek a jeho nastavení. Příklady ovládacích prvků, které implementují tento vzor najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Když implementace vzoru ovládacích prvků hodnota, poznamenejte si následující pokyny a konvence:  
  
-   Ovládací prvky jako například <xref:System.Windows.Automation.ControlType.ListItem> a <xref:System.Windows.Automation.ControlType.TreeItem> musí podporovat <xref:System.Windows.Automation.ValuePattern> Pokud hodnota některou z položek upravovat, bez ohledu na aktuální režim úprav ovládacího prvku. Nadřazeného ovládacího prvku musí také podporovat <xref:System.Windows.Automation.ValuePattern> Pokud podřízené položky se upravovat.  
  
 ![Položky seznamu upravovat. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Příklad položky seznamu upravovat  
  
-   Ovládacích prvcích pro úpravy jeden řádek podporují programový přístup k jejich obsah implementací <xref:System.Windows.Automation.Provider.IValueProvider>. Ale ovládacích prvcích pro úpravy Víceřádkový neimplementují <xref:System.Windows.Automation.Provider.IValueProvider>; místo toho poskytují přístup k jejich obsahu implementací <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
-   Můžete načíst textový obsah ovládacího prvku Víceřádkový úpravy, musí implementovat řízení <xref:System.Windows.Automation.Provider.ITextProvider>. Ale <xref:System.Windows.Automation.Provider.ITextProvider> nepodporuje nastavení hodnoty ovládacího prvku.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider>nepodporuje načtení formátování informace nebo podřetězcem hodnoty. Implementace <xref:System.Windows.Automation.Provider.ITextProvider> v těchto scénářích.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider>musí být implementované ovládací prvky, jako **volby barev** ovládacího prvku pro výběr z [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (ilustrované níže), který podporuje řetězec mapování mezi hodnotu barvu (například "žlutý") a ekvivalentní interní [!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)]struktura.  
  
 ![Výběr barvy s žlutý zvýrazněná. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Příklad mapování řetězec vzorníku barev  
  
-   Ovládacího prvku by měl mít jeho <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> nastavena na `true` a jeho <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> nastavena na `false` před povolením volání <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Požadované členy pro IValueProvider  
 Následující vlastnosti a metody jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IValueProvider>.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Metoda|Žádné|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> – Pokud informace specifické pro národní prostředí je předán do ovládacího prvku v nesprávném formátu jako je například datum nesprávně formátovaný.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> – Pokud nová hodnota nelze převést z řetězce do formátu rozpozná ovládacího prvku.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> – Když je proveden pokus o k manipulaci s ovládacího prvku, který není povolen.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Ukázka TextPattern vložení textu](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
