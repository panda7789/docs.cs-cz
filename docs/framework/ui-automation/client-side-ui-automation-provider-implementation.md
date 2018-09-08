---
title: Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: a2873fc18d5eb18160bf361b07af2bf12eef32e4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128336"
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Několik různých [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] architektury se používají v rámci [!INCLUDE[TLA#tla_ms](../../../includes/tlasharptla-ms-md.md)] operačních systémů, včetně [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] poskytuje informace o prvcích uživatelského rozhraní pro klienty. Ale [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sám nemá povědomí o různé typy ovládacích prvků, které existují v tyto architektury a techniky, které jsou potřeba k extrakci informací z nich. Místo toho ponechá tato úloha objekty nazývané poskytovatelé. Extrahuje informace z určitého ovládacího prvku zprostředkovatele a předá tyto informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], která prezentuje klientovi konzistentním způsobem.  
  
 Poskytovatelé mohou existovat na straně serveru nebo na straně klienta. Samotný ovládací prvek implementují zprostředkovatele na straně serveru. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] prvky implementace zprostředkovatelů, stejně jako všechny ovládací prvky třetích stran napsané pomocí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v úvahu.  
  
 Nicméně starší ovládací prvky, jako například sítě na [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] proveďte nemají přímou podporu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Tyto ovládací prvky jsou místo toho obsluhuje zprostředkovatelů, které existují v procesu klientů a získat informace o ovládacích prvcích pomocí komunikace mezi procesy, například při sledování zpráv systému windows do a z ovládacích prvků. Tyto zprostředkovatele na straně klienta jsou někdy označovány jako proxy servery.  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] zprostředkovatelé pro úroveň standard poskytuje [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] a ovládacích prvků Windows Forms. Kromě toho poskytuje částečné použití náhradní lokality poskytovatele [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro libovolný ovládací prvek, který není obsluhuje jiného zprostředkovatele na straně serveru nebo proxy, ale nemá [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] implementace. Tito poskytovatelé jsou automaticky načíst a dostupné pro klientské aplikace.  
  
 Další informace o podpoře pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] a ovládacích prvků Windows Forms, naleznete v tématu [uživatelského rozhraní podporu automatizace pro standardní ovládací prvky](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).  
  
 Aplikace můžete také registrovat další zprostředkovatele na straně klienta.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>Distribuce zprostředkovatele na straně klienta  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] očekává, že v sestavení spravovaného kódu najít zprostředkovatele na straně klienta. Obor názvů v tomto sestavení by měly mít stejný název jako sestavení. Například sestavení nazvané ContosoProxies.dll by obsahoval ContosoProxies oboru názvů. V rámci oboru názvů, vytvoření <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> třídy. Při provádění statické <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> pole, vytvořte pole <xref:System.Windows.Automation.ClientSideProviderDescription> struktury popisující zprostředkovatele.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Registrace a konfigurace zprostředkovatele na straně klienta  
 Zprostředkovatele na straně klienta v [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] se načítají pomocí volání <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>. Žádná další akce nevyžadovala klientskou aplikaci, aby pomocí poskytovatelů.  
  
 Implementovat v kódu klienta Vlastní zprostředkovatelé jsou registrované pomocí <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>. Tato metoda přebírá jako argument pole <xref:System.Windows.Automation.ClientSideProviderDescription> struktury, z nichž každý určuje následující vlastnosti:  
  
-   Funkce zpětného volání, která vytvoří objekt zprostředkovatele.  
  
-   Název třídy pro ovládací prvky, které bude sloužit zprostředkovatele.  
  
-   Název bitové kopie aplikace (obvykle celý název spustitelného souboru), který bude použit zprostředkovatel.  
  
-   Příznaky, které řídí, jak je název třídy hledána třídy okna v cílové aplikaci.  
  
 Poslední dva parametry jsou volitelné. Klient může zadejte název image cílové aplikace, když ji chce používat různé zprostředkovatele pro různé aplikace. Například může klient použít jednoho poskytovatele pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] seznamu ovládací prvek zobrazení ve známých aplikaci, která podporuje model více zobrazení a druhý pro podobně jako ovládací prvek v jiné známé aplikaci, která neexistuje.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích](../../../docs/framework/ui-automation/implement-ui-automation-providers-in-a-client-application.md)
