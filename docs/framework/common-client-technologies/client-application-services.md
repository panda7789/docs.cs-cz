---
title: Klientské aplikační služby
ms.date: 03/30/2017
helpviewer_keywords:
- role-based security [.NET Framework], client application services
- client application services
- credentials [.NET Framework]
- Windows-based applications, client application services
- application settings, client application services
- profiles [ASP.NET], client application services
- logins [client application services]
- sharing information and functionality [client application services]
- Web settings [client application services]
- authentication [ASP.NET], client application services
- ASP.NET services, client application services
- client applications, ASP.NET services
- roles [.NET Framework], client application services
- client application services, about client application services
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
ms.openlocfilehash: d67b7467bdacdfca054d0ecd11a81c7d25b158f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743222"
---
# <a name="client-application-services"></a>Klientské aplikační služby
Klient aplikačních služeb můžete snadno vytvořit aplikace systému Windows, které používají [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] přihlášení, rolí a součástí rozšíření Microsoft ASP.NET 2.0 AJAX profil aplikačních služeb. Tyto služby umožňují více Web a aplikace pro systém Windows sdílet informace o uživateli a správu uživatelů funkci z jednoho serveru. Tyto služby můžete například použít k provádění následujících úloh:  
  
-   Ověření uživatele. Služba ověřování můžete použít k ověření identity uživatele.  
  
-   Určení roli nebo role ověřeného uživatele. Chcete-li změnit uživatelské rozhraní aplikace, v závislosti na roli uživatele, můžete použít službu role. Například můžete zadat další funkce pro uživatele, kteří jsou v roli správce.  
  
-   Úložiště a přístup uživatelská nastavení aplikací umístěný na serveru. Nastavení webové služby (také označované jako služba profilu) můžete sdílet nastavení mezi více aplikací a umístění.  
  
 Klient aplikačních služeb využít model webových služeb rozšiřitelnost prostřednictvím poskytovatelů služeb klienta, které můžete zadat v konfiguračních souborech aplikace. Poskytovatelé služeb mají offline funkci, které používá místní mezipaměti pro ověřování, rolí a nastavení dat, když není k dispozici síťové připojení.  
  
 Další informace o [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] aplikační služby, najdete v části [aplikace ASP.NET: Přehled služby](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 Popisuje funkce, které jsou k dispozici prostřednictvím poskytovatelů služeb aplikací klienta.  
  
 [Postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 Popisuje, jak používat Návrhář projektu sady Visual Studio k povolení a konfigurace aplikační služby. Také popisuje odpovídající změny do souboru App.config.  
  
 [Postupy: Implementace přihlášení uživatele u klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 Popisuje, jak ověřit uživatele, pokud je vaše aplikace nakonfigurovaná pro použití poskytovatele služby ověřování klienta.  
  
 [Návod: Použití klientských aplikačních služeb](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 Popisuje postup kombinace všechny funkce služby v jedné aplikaci klientské aplikace. Tento názorný postup obsahuje pokyny začátku do konce. Například obsahuje pokyny k vytvoření aplikace ASP.NET webové služby, který můžete použít k testování klientské aplikační služby.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Web.ClientServices.ClientFormsIdentity>  
 <xref:System.Web.ClientServices.ClientRolePrincipal>  
 <xref:System.Web.ClientServices.ConnectivityStatus>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>  
 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientRoleProvider>  
 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider>  
 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>  
 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>  
  
## <a name="see-also"></a>Viz také  
 [Přehled služby aplikace ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Použití ověřování pomocí formulářů s technologií Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Pomocí informací o rolí s technologií Microsoft Ajax](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Informace o profilu pomocí Microsoft Ajax](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [Ověřování pomocí technologie ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Řízení autorizací pomocí rolí](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)    
 [Přehled nastavení aplikace](../../../docs/framework/winforms/advanced/application-settings-overview.md)
