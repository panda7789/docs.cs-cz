---
title: 'Postupy: Určení kontextu zabezpečení pro služby'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
ms.openlocfilehash: 0b011497d04a1da3764b75c4d8c5d7084ff110bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154047"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="e3fb0-102">Postupy: Určení kontextu zabezpečení pro služby</span><span class="sxs-lookup"><span data-stu-id="e3fb0-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="e3fb0-103">Ve výchozím nastavení služby jsou spuštěny v kontextu zabezpečení než přihlášeným uživatelem.</span><span class="sxs-lookup"><span data-stu-id="e3fb0-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="e3fb0-104">Volá se spouštějí v kontextu systému výchozí účet služby `LocalSystem`, která jim udělí různá přístupová oprávnění k systémových prostředků, než uživatel.</span><span class="sxs-lookup"><span data-stu-id="e3fb0-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="e3fb0-105">Toto chování k určení jiného uživatelského účtu, pod kterým se vaše služba spouštět můžete změnit.</span><span class="sxs-lookup"><span data-stu-id="e3fb0-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="e3fb0-106">Nastavte kontext zabezpečení manipulací <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost pro proces, ve kterém je služba spuštěna.</span><span class="sxs-lookup"><span data-stu-id="e3fb0-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="e3fb0-107">Tato vlastnost umožňuje nastavit službu do jedné ze čtyř typů účtu:</span><span class="sxs-lookup"><span data-stu-id="e3fb0-107">This property allows you to set the service to one of four account types:</span></span>  
  
-   `User`<span data-ttu-id="e3fb0-108">, což způsobí, že systém výzvy platné uživatelské jméno a heslo, pokud služba je nainstalována a spuštěna v kontextu účet specifikovaný v síti; jedním uživatelem</span><span class="sxs-lookup"><span data-stu-id="e3fb0-108">, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
-   `LocalService`<span data-ttu-id="e3fb0-109">, která se spouští v kontextu účtu, který funguje jako neprivilegované uživatele v místním počítači a nabízí pověření anonymního a jakémukoli vzdálenému serveru;</span><span class="sxs-lookup"><span data-stu-id="e3fb0-109">, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
-   `LocalSystem`<span data-ttu-id="e3fb0-110">, která se spouští v kontextu účtu, který poskytuje rozsáhlé místní oprávnění a zobrazení přihlašovacích údajů počítače a jakémukoli vzdálenému serveru;</span><span class="sxs-lookup"><span data-stu-id="e3fb0-110">, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
-   `NetworkService`<span data-ttu-id="e3fb0-111">, která se spouští v kontextu účtu, který funguje jako neprivilegované uživatele v místním počítači a uvede přihlašovacích údajů počítače a jakémukoli vzdálenému serveru.</span><span class="sxs-lookup"><span data-stu-id="e3fb0-111">, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="e3fb0-112">Další informace najdete v tématu <xref:System.ServiceProcess.ServiceAccount> výčtu.</span><span class="sxs-lookup"><span data-stu-id="e3fb0-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="e3fb0-113">K určení kontextu zabezpečení pro službu</span><span class="sxs-lookup"><span data-stu-id="e3fb0-113">To specify the security context for a service</span></span>  
  
1.  <span data-ttu-id="e3fb0-114">Po vytvoření vaší služby, přidejte nezbytné instalační programy pro něj.</span><span class="sxs-lookup"><span data-stu-id="e3fb0-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="e3fb0-115">Další informace najdete v tématu [jak: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="e3fb0-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="e3fb0-116">V návrháři pro přístup `ProjectInstaller` třídy a klikněte na instalační program služby procesu pro službu pracujete.</span><span class="sxs-lookup"><span data-stu-id="e3fb0-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3fb0-117">Pro každou aplikaci služby existují alespoň dvě součásti instalace v `ProjectInstaller` třídy – ten, který nainstaluje procesy pro všechny služby v projektu a jednoho instalačního programu pro každou službu, která obsahuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e3fb0-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="e3fb0-118">V této instanci, kterou chcete vybrat <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="e3fb0-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3.  <span data-ttu-id="e3fb0-119">V **vlastnosti** okno, nastaveno <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e3fb0-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3fb0-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3fb0-120">See also</span></span>

- [<span data-ttu-id="e3fb0-121">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="e3fb0-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="e3fb0-122">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="e3fb0-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="e3fb0-123">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="e3fb0-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
