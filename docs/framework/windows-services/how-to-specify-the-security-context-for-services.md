---
title: "Postupy: Určení kontextu zabezpečení pro služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 9ce65358f6d63414dbe6798d3cc2464ee2741980
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="b48af-102">Postupy: Určení kontextu zabezpečení pro služby</span><span class="sxs-lookup"><span data-stu-id="b48af-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="b48af-103">Ve výchozím nastavení služby spuštěny v odlišném kontextu zabezpečení než přihlášeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="b48af-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="b48af-104">Volá se spouštějí v kontextu systému do výchozího účtu služby `LocalSystem`, která jim udělí různých přístupová oprávnění k systémovým prostředkům než uživatele.</span><span class="sxs-lookup"><span data-stu-id="b48af-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="b48af-105">Toto chování zadat jiný uživatelský účet, pod kterým měly být spuštěny služby, můžete změnit.</span><span class="sxs-lookup"><span data-stu-id="b48af-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="b48af-106">Nastavit kontext zabezpečení manipulací <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost pro proces, ve kterém je služba spuštěna.</span><span class="sxs-lookup"><span data-stu-id="b48af-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="b48af-107">Tato vlastnost umožňuje nastavit na jedno ze čtyř typů účet služby:</span><span class="sxs-lookup"><span data-stu-id="b48af-107">This property allows you to set the service to one of four account types:</span></span>  
  
-   <span data-ttu-id="b48af-108">`User`, což způsobí, že systém výzvy platné uživatelské jméno a heslo, pokud služba je nainstalován a spuštěn v kontextu účtu určeného jenom jednoho konkrétního uživatele v síti;</span><span class="sxs-lookup"><span data-stu-id="b48af-108">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
-   <span data-ttu-id="b48af-109">`LocalService`, který běží v kontextu účtu, který funguje jako uživatel bez oprávnění místního počítače a uvede anonymní přihlašovací údaje k žádnému vzdáleného serveru;</span><span class="sxs-lookup"><span data-stu-id="b48af-109">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="b48af-110">`LocalSystem`, který běží v kontextu účtu, který poskytuje rozsáhlé místní oprávnění a zobrazení počítače přihlašovací údaje k žádnému vzdáleného serveru;</span><span class="sxs-lookup"><span data-stu-id="b48af-110">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="b48af-111">`NetworkService`, který běží v kontextu účtu, který funguje jako uživatel bez oprávnění v místním počítači a uvede počítače přihlašovací údaje k žádnému vzdáleného serveru.</span><span class="sxs-lookup"><span data-stu-id="b48af-111">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="b48af-112">Další informace najdete v tématu <xref:System.ServiceProcess.ServiceAccount> výčtu.</span><span class="sxs-lookup"><span data-stu-id="b48af-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="b48af-113">Chcete-li určit kontext zabezpečení pro službu</span><span class="sxs-lookup"><span data-stu-id="b48af-113">To specify the security context for a service</span></span>  
  
1.  <span data-ttu-id="b48af-114">Po vytvoření služby, přidejte potřebné instalační programy pro ni.</span><span class="sxs-lookup"><span data-stu-id="b48af-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="b48af-115">Další informace najdete v tématu [postupy: Přidání instalačních programů pro vaše aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="b48af-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="b48af-116">V návrháři přístup `ProjectInstaller` třídu a klikněte na instalační program služby procesu pro službu pracujete.</span><span class="sxs-lookup"><span data-stu-id="b48af-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b48af-117">Pro každou aplikaci služby existují alespoň dvě součásti instalace v `ProjectInstaller` třída – jeden, který nainstaluje procesy pro všechny služby v projektu a jeden instalační program pro každou službu, která obsahuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b48af-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="b48af-118">V této instanci, kterou chcete vybrat <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="b48af-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3.  <span data-ttu-id="b48af-119">V **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b48af-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48af-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b48af-120">See Also</span></span>  
 [<span data-ttu-id="b48af-121">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="b48af-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="b48af-122">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="b48af-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="b48af-123">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="b48af-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
