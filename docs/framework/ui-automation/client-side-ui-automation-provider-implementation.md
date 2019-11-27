---
title: Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 03df282022c39673a7e160dd5d79bdadd0c7adda
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433992"
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 V operačních systémech Microsoftu se používá několik různých [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] platforem, včetně [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zpřístupňuje klientům informace o prvcích uživatelského rozhraní. Nicméně [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sám o sobě nepovědomí o různých typech ovládacích prvků, které existují v těchto rozhraních, a metodách, které jsou potřebné k extrakci informací z nich. Místo toho tento úkol opustí objekty označované jako zprostředkovatelé. Zprostředkovatel extrahuje informace z konkrétního ovládacího prvku a zavolá tyto informace pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], které je následně prezentuje klientovi konzistentním způsobem.  
  
 Poskytovatelé můžou existovat buď na straně serveru, nebo na straně klienta. Poskytovatel na straně serveru je implementovaný samotným ovládacím prvkem. prvky [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] implementují poskytovatele, stejně jako mohou jakékoli ovládací prvky třetích stran zapsané s [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 Starší ovládací prvky, jako jsou například [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], však přímo nepodporují [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Tyto ovládací prvky se místo toho obsluhují poskytovateli, kteří existují v procesu klienta, a získávají informace o ovládacích prvcích pomocí komunikace mezi procesy. například monitorováním zpráv systému Windows do a z ovládacích prvků. Tito poskytovatelé na straně klienta jsou někdy označováni jako proxy.  
  
 Systém Windows Vista dodává poskytovatele pro standardní [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] a model Windows Forms ovládací prvky. Záložní zprostředkovatel navíc poskytuje částečnou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro jakýkoli ovládací prvek, který není obsluhován jiným poskytovatelem na straně serveru nebo proxy serverem, ale má implementaci Microsoft Active Accessibility. Všichni tito poskytovatelé jsou automaticky načítáni a k dispozici pro klientské aplikace.  
  
 Další informace o podpoře pro ovládací prvky [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] a model Windows Forms najdete v tématu [Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky](ui-automation-support-for-standard-controls.md).  
  
 Aplikace také mohou registrovat jiné poskytovatele na straně klienta.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>Distribuce poskytovatelů na straně klienta  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] očekává hledání poskytovatelů na straně klienta v sestavení spravovaného kódu. Obor názvů v tomto sestavení by měl mít stejný název jako sestavení. Například sestavení s názvem ContosoProxies. dll by obsahovalo obor názvů ContosoProxies. V rámci oboru názvů vytvořte třídu <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders>. V implementaci pole static <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> vytvořte pole <xref:System.Windows.Automation.ClientSideProviderDescription> struktury, které popisují poskytovatele.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Registrace a konfigurace poskytovatelů na straně klienta  
 Poskytovatelé na straně klienta v dynamické knihovně (DLL) jsou načítány voláním <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>. Klientská aplikace nepotřebuje k používání poskytovatelů žádnou další akci.  
  
 Poskytovatelé implementující ve vlastním kódu klienta jsou registrováni pomocí <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>. Tato metoda přijímá jako argument pole <xref:System.Windows.Automation.ClientSideProviderDescription> struktury, z nichž každý určuje následující vlastnosti:  
  
- Funkce zpětného volání, která vytvoří objekt poskytovatele.  
  
- Název třídy ovládacích prvků, které bude poskytovat poskytovatel.  
  
- Název Image aplikace (obvykle úplný název spustitelného souboru), který bude poskytovat poskytovatel.  
  
- Příznaky, které určují, jak se název třídy shoduje s třídami oken nalezenými v cílové aplikaci.  
  
 Poslední dva parametry jsou volitelné. Klient může zadat název Image cílové aplikace, když chce použít různé poskytovatele pro různé aplikace. Klient může například použít jednoho poskytovatele pro ovládací prvek zobrazení seznamu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ve známé aplikaci, která podporuje vzor vícenásobného zobrazení, a druhý pro podobný ovládací prvek v jiné známé aplikaci, která ne.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta](create-a-client-side-ui-automation-provider.md)
- [Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích](implement-ui-automation-providers-in-a-client-application.md)
