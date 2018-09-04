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
ms.openlocfilehash: d58510240593f73ff761aa669035f28598006c10
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521997"
---
# <a name="client-application-services"></a>Klientské aplikační služby
Klientské aplikační služby umožňují snadno vytvářet aplikace pro systém Windows, které používají [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] přihlášení, role a služby profilu aplikace součástí rozšíření společnosti Microsoft 2.0 technologie ASP.NET AJAX. Tyto služby umožňují více webových a aplikace založené na Windows sdílet informace o uživateli a funkci Správa uživatelů z jednoho serveru. Tyto služby můžete například používat k provádění následujících úloh:  
  
-   Ověření uživatele. Služba ověřování můžete použít k ověření identity uživatele.  
  
-   Zjistěte, role nebo role ověřeného uživatele. Chcete-li změnit uživatelské rozhraní vaší aplikace v závislosti na roli uživatele můžete použít službu role. Například můžete zadat další funkce pro uživatele, kteří jsou v roli správce.  
  
-   Store a přístup k aplikaci nastavení pro jednotlivé uživatele na serveru. Nastavení webové služby (označované také jako službu profilů) můžete použít ke sdílení nastavení mezi různými aplikacemi a umístění.  
  
 Klientské aplikační služby využívat model webových služeb rozšiřitelnost prostřednictvím poskytovatelů služeb klienta, které můžete zadat v konfiguračních souborech aplikace. Poskytovatelé služeb zahrnují offline funkce, která používá místní mezipaměť pro ověřování, role a nastavení dat, když není k dispozici připojení k síti.  
  
 Další informace o [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] aplikační služby, najdete v článku [přehled aplikačních služeb ASP.NET](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 Popisuje funkce dostupné prostřednictvím poskytovatelů služeb aplikací klienta.  
  
 [Postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 Popisuje způsob použití Návrháře projektu sady Visual Studio k povolení a konfigurace aplikační služby. Také popisuje odpovídající změny do souboru App.config.  
  
 [Postupy: Implementace přihlášení uživatele u klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 Popisuje, jak ověřit uživatele, pokud vaše aplikace je nakonfigurovaná pro použití služby poskytovatele ověřování klienta.  
  
 [Návod: Použití klientských aplikačních služeb](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 Popisuje, jak kombinovat všechny funkce klienta aplikace služby v jedné aplikaci. Tento názorný postup obsahuje pokyny k začátku do konce. Například obsahuje pokyny k vytvoření aplikace ASP.NET Web Service, můžete použít k testování klientských aplikačních služeb.  
  
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
 [Přehled aplikačních služeb technologie ASP.NET](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Ověřování pomocí formulářů s technologií Microsoft Ajax](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Informace o roli pomocí Microsoft Ajax](https://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Pomocí informací o profilu Microsoft Ajax](https://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [Ověřování pomocí technologie ASP.NET](https://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Správa autorizací pomocí rolí](https://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)    
 [Přehled nastavení aplikace](../../../docs/framework/winforms/advanced/application-settings-overview.md)
