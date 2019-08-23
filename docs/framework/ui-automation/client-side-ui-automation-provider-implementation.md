---
title: Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: dd5f744a67481b03802887ff2baa0571b30e4b5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965238"
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 V [!INCLUDE[TLA#tla_ms](../../../includes/tlasharptla-ms-md.md)] operačních [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] systémech se používá několik různých platforem, včetně [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]zpřístupňuje informace o prvcích uživatelského rozhraní pro klienty. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Nicméně nemá na vědomí různé typy ovládacích prvků, které existují v těchto rozhraních, a techniky, které jsou potřebné k extrakci informací z nich. Místo toho tento úkol opustí objekty označované jako zprostředkovatelé. Poskytovatel extrahuje informace z konkrétního ovládacího prvku a zaznamená si [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informace, které je pak zaprezentuje klientovi konzistentním způsobem.  
  
 Poskytovatelé můžou existovat buď na straně serveru, nebo na straně klienta. Poskytovatel na straně serveru je implementovaný samotným ovládacím prvkem. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]prvky implementují poskytovatele, stejně jako mohou jakékoli ovládací prvky třetích stran [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , které jsou zapsány na mysli.  
  
 Starší ovládací prvky, jako jsou například v [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] nástroji [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] a přímo nepodporují [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Tyto ovládací prvky se místo toho obsluhují poskytovateli, kteří existují v procesu klienta, a získávají informace o ovládacích prvcích pomocí komunikace mezi procesy. například monitorováním zpráv systému Windows do a z ovládacích prvků. Tito poskytovatelé na straně klienta jsou někdy označováni jako proxy.  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]poskytovatelé poskytování pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] standardní ovládací prvky a model Windows Forms. Záložní zprostředkovatel navíc poskytuje částečnou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro jakýkoli ovládací prvek, který není obsluhován jiným poskytovatelem na straně serveru nebo proxy serverem, ale má implementaci Microsoft Active Accessibility. Všichni tito poskytovatelé jsou automaticky načítáni a k dispozici pro klientské aplikace.  
  
 Další informace o podpoře [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] a model Windows Forms ovládacích prvcích najdete v tématu [Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).  
  
 Aplikace také mohou registrovat jiné poskytovatele na straně klienta.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>Distribuce poskytovatelů na straně klienta  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]očekává, že se v sestavení spravovaného kódu vyhledají poskytovatelé na straně klienta. Obor názvů v tomto sestavení by měl mít stejný název jako sestavení. Například sestavení s názvem ContosoProxies. dll by obsahovalo obor názvů ContosoProxies. V rámci oboru názvů vytvořte <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> třídu. V implementaci statického <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> pole vytvořte pole struktury, které <xref:System.Windows.Automation.ClientSideProviderDescription> popisují poskytovatele.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Registrace a konfigurace poskytovatelů na straně klienta  
 Zprostředkovatelé na straně klienta v dynamické knihovně (DLL) jsou načítány voláním metody <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>. Klientská aplikace nepotřebuje k používání poskytovatelů žádnou další akci.  
  
 Poskytovatelé implementující ve vlastním kódu klienta jsou registrováni pomocí <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>. Tato metoda přijímá jako argument pole <xref:System.Windows.Automation.ClientSideProviderDescription> struktur, z nichž každý určuje následující vlastnosti:  
  
- Funkce zpětného volání, která vytvoří objekt poskytovatele.  
  
- Název třídy ovládacích prvků, které bude poskytovat poskytovatel.  
  
- Název Image aplikace (obvykle úplný název spustitelného souboru), který bude poskytovat poskytovatel.  
  
- Příznaky, které určují, jak se název třídy shoduje s třídami oken nalezenými v cílové aplikaci.  
  
 Poslední dva parametry jsou volitelné. Klient může zadat název Image cílové aplikace, když chce použít různé poskytovatele pro různé aplikace. Klient může například použít jednoho poskytovatele pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvek zobrazení seznamu ve známé aplikaci, která podporuje vzorek více zobrazení, a druhý pro podobný ovládací prvek v jiné známé aplikaci, která ne.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích](../../../docs/framework/ui-automation/implement-ui-automation-providers-in-a-client-application.md)
