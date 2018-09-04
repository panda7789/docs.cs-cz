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
# <a name="client-application-services"></a><span data-ttu-id="fbfca-102">Klientské aplikační služby</span><span class="sxs-lookup"><span data-stu-id="fbfca-102">Client Application Services</span></span>
<span data-ttu-id="fbfca-103">Klientské aplikační služby umožňují snadno vytvářet aplikace pro systém Windows, které používají [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] přihlášení, role a služby profilu aplikace součástí rozšíření společnosti Microsoft 2.0 technologie ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="fbfca-103">Client application services make it easy for you to create Windows-based applications that use the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] login, roles, and profile application services included in the Microsoft ASP.NET 2.0 AJAX Extensions.</span></span> <span data-ttu-id="fbfca-104">Tyto služby umožňují více webových a aplikace založené na Windows sdílet informace o uživateli a funkci Správa uživatelů z jednoho serveru.</span><span class="sxs-lookup"><span data-stu-id="fbfca-104">These services enable multiple Web and Windows-based applications to share user information and user-management functionality from a single server.</span></span> <span data-ttu-id="fbfca-105">Tyto služby můžete například používat k provádění následujících úloh:</span><span class="sxs-lookup"><span data-stu-id="fbfca-105">For example, you can use these services to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="fbfca-106">Ověření uživatele.</span><span class="sxs-lookup"><span data-stu-id="fbfca-106">Authenticate a user.</span></span> <span data-ttu-id="fbfca-107">Služba ověřování můžete použít k ověření identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="fbfca-107">You can use the authentication service to verify a user's identity.</span></span>  
  
-   <span data-ttu-id="fbfca-108">Zjistěte, role nebo role ověřeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="fbfca-108">Determine the role or roles of an authenticated user.</span></span> <span data-ttu-id="fbfca-109">Chcete-li změnit uživatelské rozhraní vaší aplikace v závislosti na roli uživatele můžete použít službu role.</span><span class="sxs-lookup"><span data-stu-id="fbfca-109">You can use the roles service to change the user interface of your application depending on the user's role.</span></span> <span data-ttu-id="fbfca-110">Například můžete zadat další funkce pro uživatele, kteří jsou v roli správce.</span><span class="sxs-lookup"><span data-stu-id="fbfca-110">For example, you can provide additional features for users who are in an administrator role.</span></span>  
  
-   <span data-ttu-id="fbfca-111">Store a přístup k aplikaci nastavení pro jednotlivé uživatele na serveru.</span><span class="sxs-lookup"><span data-stu-id="fbfca-111">Store and access per-user application settings located on the server.</span></span> <span data-ttu-id="fbfca-112">Nastavení webové služby (označované také jako službu profilů) můžete použít ke sdílení nastavení mezi různými aplikacemi a umístění.</span><span class="sxs-lookup"><span data-stu-id="fbfca-112">You can use the Web settings service (also known as the profile service) to share settings across multiple applications and locations.</span></span>  
  
 <span data-ttu-id="fbfca-113">Klientské aplikační služby využívat model webových služeb rozšiřitelnost prostřednictvím poskytovatelů služeb klienta, které můžete zadat v konfiguračních souborech aplikace.</span><span class="sxs-lookup"><span data-stu-id="fbfca-113">Client application services take advantage of the Web services extensibility model through client service providers that you can specify in your application configuration files.</span></span> <span data-ttu-id="fbfca-114">Poskytovatelé služeb zahrnují offline funkce, která používá místní mezipaměť pro ověřování, role a nastavení dat, když není k dispozici připojení k síti.</span><span class="sxs-lookup"><span data-stu-id="fbfca-114">These service providers include offline functionality that uses a local cache for authentication, roles, and settings data when a network connection is unavailable.</span></span>  
  
 <span data-ttu-id="fbfca-115">Další informace o [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] aplikační služby, najdete v článku [přehled aplikačních služeb ASP.NET](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span><span class="sxs-lookup"><span data-stu-id="fbfca-115">For more information about the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] application services, see [ASP.NET Application Services Overview](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fbfca-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fbfca-116">In This Section</span></span>  
 [<span data-ttu-id="fbfca-117">Přehled klientských aplikačních služeb</span><span class="sxs-lookup"><span data-stu-id="fbfca-117">Client Application Services Overview</span></span>](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 <span data-ttu-id="fbfca-118">Popisuje funkce dostupné prostřednictvím poskytovatelů služeb aplikací klienta.</span><span class="sxs-lookup"><span data-stu-id="fbfca-118">Describes the features available through the client application service providers.</span></span>  
  
 [<span data-ttu-id="fbfca-119">Postupy: Konfigurace klientských aplikačních služeb</span><span class="sxs-lookup"><span data-stu-id="fbfca-119">How to: Configure Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 <span data-ttu-id="fbfca-120">Popisuje způsob použití Návrháře projektu sady Visual Studio k povolení a konfigurace aplikační služby.</span><span class="sxs-lookup"><span data-stu-id="fbfca-120">Describes how to use the Visual Studio project designer to enable and configuration application services.</span></span> <span data-ttu-id="fbfca-121">Také popisuje odpovídající změny do souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="fbfca-121">Also describes the corresponding changes to your App.config file.</span></span>  
  
 [<span data-ttu-id="fbfca-122">Postupy: Implementace přihlášení uživatele u klientských aplikačních služeb</span><span class="sxs-lookup"><span data-stu-id="fbfca-122">How to: Implement User Login with Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 <span data-ttu-id="fbfca-123">Popisuje, jak ověřit uživatele, pokud vaše aplikace je nakonfigurovaná pro použití služby poskytovatele ověřování klienta.</span><span class="sxs-lookup"><span data-stu-id="fbfca-123">Describes how to validate a user when your application is configured to use a client authentication service provider.</span></span>  
  
 [<span data-ttu-id="fbfca-124">Návod: Použití klientských aplikačních služeb</span><span class="sxs-lookup"><span data-stu-id="fbfca-124">Walkthrough: Using Client Application Services</span></span>](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 <span data-ttu-id="fbfca-125">Popisuje, jak kombinovat všechny funkce klienta aplikace služby v jedné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fbfca-125">Describes how to combine all client application services features in a single application.</span></span> <span data-ttu-id="fbfca-126">Tento názorný postup obsahuje pokyny k začátku do konce.</span><span class="sxs-lookup"><span data-stu-id="fbfca-126">This walkthrough provides end-to-end guidance.</span></span> <span data-ttu-id="fbfca-127">Například obsahuje pokyny k vytvoření aplikace ASP.NET Web Service, můžete použít k testování klientských aplikačních služeb.</span><span class="sxs-lookup"><span data-stu-id="fbfca-127">For example, it includes instructions on how to create an ASP.NET Web Service Application that you can use to test client application services.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fbfca-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="fbfca-128">Reference</span></span>  
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
  
## <a name="see-also"></a><span data-ttu-id="fbfca-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbfca-129">See Also</span></span>  
 [<span data-ttu-id="fbfca-130">Přehled aplikačních služeb technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fbfca-130">ASP.NET Application Services Overview</span></span>](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [<span data-ttu-id="fbfca-131">Ověřování pomocí formulářů s technologií Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="fbfca-131">Using Forms Authentication with Microsoft Ajax</span></span>](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [<span data-ttu-id="fbfca-132">Informace o roli pomocí Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="fbfca-132">Using Roles Information with Microsoft Ajax</span></span>](https://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [<span data-ttu-id="fbfca-133">Pomocí informací o profilu Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="fbfca-133">Using Profile Information with Microsoft Ajax</span></span>](https://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [<span data-ttu-id="fbfca-134">Ověřování pomocí technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fbfca-134">ASP.NET Authentication</span></span>](https://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 <span data-ttu-id="fbfca-135">[Správa autorizací pomocí rolí](https://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span><span class="sxs-lookup"><span data-stu-id="fbfca-135">[Managing Authorization Using Roles](https://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span></span>  
 [<span data-ttu-id="fbfca-136">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="fbfca-136">Application Settings Overview</span></span>](../../../docs/framework/winforms/advanced/application-settings-overview.md)
