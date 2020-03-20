---
title: Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 50d7921f1c63580248b562864f9c1f398d41c9bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180260"
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implementace zprostředkovatele automatizace uživatelského rozhraní na straně klienta
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 V [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] operačních systémech Microsoft se používá několik různých architektur, včetně [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]win32, windows forms a . [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]zpřístupňuje klientům informace o prvcích uživatelského rozhraní. Nicméně [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nemá povědomí o různých typech ovládacích prvků, které existují v těchto rámců a techniky, které jsou potřebné k získání informací z nich. Místo toho ponechá tuto úlohu na objekty nazývané zprostředkovatelé. Zprostředkovatel extrahuje informace z konkrétní ovládací [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]prvek a ruce, které informace , který pak prezentuje klientovi konzistentním způsobem.  
  
 Zprostředkovatelé mohou existovat na straně serveru nebo na straně klienta. Zprostředkovatel na straně serveru je implementován samotným ovládacím prvkem. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]prvky implementovat zprostředkovatele, stejně [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jako všechny ovládací prvky třetích stran napsané s ohledem.  
  
 Starší ovládací prvky, například ve windows 32 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]a Windows Forms, však přímo nepodporují . Tyto ovládací prvky jsou obsluhovány místo zprostředkovatelů, které existují v procesu klienta a získat informace o ovládacích prvcích pomocí komunikace mezi procesy; například sledováním zpráv systému Windows do a z ovládacích prvků. Takové zprostředkovatele na straně klienta se někdy nazývají proxy servery.  
  
 Systém Windows Vista poskytuje zprostředkovatele standardních ovládacích prvků Win32 a Windows Forms. Záložní zprostředkovatel navíc poskytuje částečnou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu libovolnému ovládacímu prvku, který není obsluhován jiným poskytovatelem nebo proxy serverem, ale má implementaci microsoft active accessibility. Všichni tito zprostředkovatelé jsou automaticky načteni a k dispozici klientským aplikacím.  
  
 Další informace o podpoře ovládacích prvků Win32 a Windows Forms naleznete v [tématu Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky](ui-automation-support-for-standard-controls.md).  
  
 Aplikace mohou také zaregistrovat další zprostředkovatele na straně klienta.  
  
<a name="Distributing_Client-Side_Providers"></a>
## <a name="distributing-client-side-providers"></a>Distribuce zprostředkovatelů na straně klienta  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]očekává, že najít zprostředkovatele na straně klienta v sestavení spravovaného kódu. Obor názvů v tomto sestavení by měl mít stejný název jako sestavení. Například sestavení s názvem ContosoProxies.dll by obsahovalo obor názvů ContosoProxies. V oboru názvů vytvořte třídu. <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> Při implementaci statického <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> pole vytvořte <xref:System.Windows.Automation.ClientSideProviderDescription> pole struktur popisujících zprostředkovatele.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>
## <a name="registering-and-configuring-client-side-providers"></a>Registrace a konfigurace zprostředkovatelů na straně klienta  
 Zprostředkovatelé na straně klienta v dynamicko-linkové <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>knihovně (DLL) jsou načteni voláním . Klientská aplikace nevyžaduje žádnou další akci, aby využila zprostředkovatele.  
  
 Zprostředkovatelé implementovaní ve vlastním kódu <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>klienta jsou registrováni pomocí . Tato metoda bere jako argument <xref:System.Windows.Automation.ClientSideProviderDescription> pole struktur, z nichž každá určuje následující vlastnosti:  
  
- Funkce zpětného volání, která vytvoří objekt zprostředkovatele.  
  
- Název třídy ovládacích prvků, které bude obsluhuje zprostředkovatele.  
  
- Název obrázku aplikace (obvykle úplný název spustitelného souboru), který bude poskytovatel obsluhovat.  
  
- Příznaky, které řídí, jak je název třídy porovnán s třídami oken nalezenými v cílové aplikaci.  
  
 Poslední dva parametry jsou volitelné. Klient může zadat název bitové kopie cílové aplikace, pokud chce použít různé zprostředkovatele pro různé aplikace. Klient může například použít jednoho zprostředkovatele pro ovládací prvek zobrazení seznamu Win32 ve známé aplikaci, která podporuje vzor více zobrazení a jiný pro podobný ovládací prvek v jiné známé aplikaci, která není.  
  
## <a name="see-also"></a>Viz také

- [Vytvoření zprostředkovatele automatizace uživatelského rozhraní na straně klienta](create-a-client-side-ui-automation-provider.md)
- [Implementace zprostředkovatelů automatizace uživatelského rozhraní v klientských aplikacích](implement-ui-automation-providers-in-a-client-application.md)
