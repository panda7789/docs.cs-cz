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
ms.openlocfilehash: 0e1a8e6820d70e4c50599056e31563f7f792f6d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400104"
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Několik různých [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] rozhraní se používají v rámci [!INCLUDE[TLA#tla_ms](../../../includes/tlasharptla-ms-md.md)] operačních systémů, včetně [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zpřístupní informace o prvky uživatelského rozhraní pro klienty. Ale [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] není sám nemá povědomí o různé typy ovládacích prvků, které existují v těchto rozhraní a techniky, které jsou potřebné k extrakci informací z nich. Místo toho ponechá tuto úlohu na objekty nazývané poskytovatelé. Zprostředkovatel získá informace ze určitý ovládací prvek a předá tyto informace k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], který pak ji uvede klientovi konzistentním způsobem.  
  
 Zprostředkovatelé může existovat na straně serveru nebo na straně klienta. Na straně serveru zprostředkovatele je implementováno modulem samotném ovládacím prvku. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy implementovat poskytovatelů, jak můžete všechny ovládací prvky třetích stran napsané pomocí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v paměti.  
  
 Ale starší ovládací prvky, jako jsou ty v [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] provést není přímo podporu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Tyto ovládací prvky se zpracovávají místo zprostředkovatelé, které existují v procesu klienta a získat informace o ovládacích prvků pomocí komunikace mezi procesy; například sledováním zpráv systému windows do a z ovládacích prvků. Poskytovatelé klienta se někdy označuje jako proxy servery.  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] nabízí poskytovatele pro standardní [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] a ovládací prvky Windows Forms. Kromě toho poskytuje částečné záložní zprostředkovatele [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro libovolný ovládací prvek, který není obsluhován jiného zprostředkovatele na straně serveru nebo proxy, ale má [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] implementace. Všechny tyto zprostředkovatele jsou automaticky načíst a k dispozici pro klientské aplikace.  
  
 Další informace o podporu pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] a ovládací prvky Windows Forms, najdete v části [uživatelského rozhraní automatizace podpora pro standardní ovládací prvky](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).  
  
 Aplikace lze také zaregistrovat jiných poskytovatelů na straně klienta.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>Distribuce zprostředkovatele na straně klienta  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Očekává se najít zprostředkovatele na straně klienta v sestavení spravovaného kódu. Obor názvů v tomto sestavení musí mít stejný název jako sestavení. Sestavení nazvané ContosoProxies.dll by například obsahovat ContosoProxies obor názvů. V rámci oboru názvů, vytvoření <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> třídy. Při provádění statických <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> pole, vytvořte pole <xref:System.Windows.Automation.ClientSideProviderDescription> struktury, které popisují zprostředkovatele.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Registrace a konfigurace zprostředkovatele na straně klienta  
 Zprostředkovatele na straně klienta v [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] se načtou při volání <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>. Žádná další akce je klientská aplikace, aby se vyžaduje použití zprostředkovatele.  
  
 Zprostředkovatelé implementovat v kódu klienta vlastní jsou zaregistrovány pomocí <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>. Tato metoda přijímá jako argument pole <xref:System.Windows.Automation.ClientSideProviderDescription> struktury, z nichž každý určuje následující vlastnosti:  
  
-   Funkce zpětného volání, která vytvoří objekt zprostředkovatele.  
  
-   Název třídy ovládacích prvků, které bude sloužit zprostředkovatele.  
  
-   Název bitové kopie aplikace (obvykle úplný název spustitelného souboru), která bude sloužit zprostředkovatele.  
  
-   Příznaky, které řídí, jak je název třídy shoda na základě třídy oken nalezen v cílové aplikaci.  
  
 Poslední dva parametry jsou volitelné. Klient může zadejte název bitové kopie cílová aplikace, když chce používat různé zprostředkovatele pro různé aplikace. Například může klient použít jednoho poskytovatele pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvek v známé aplikace, která podporuje vzoru více zobrazení a další podobné ovládacího prvku v jiné známé aplikaci, která neprovádí seznamu.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích](../../../docs/framework/ui-automation/implement-ui-automation-providers-in-a-client-application.md)
