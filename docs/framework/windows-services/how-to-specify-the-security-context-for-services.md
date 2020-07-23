---
title: 'Postupy: Určení kontextu zabezpečení pro služby'
description: Určete kontext zabezpečení pro služby. Služby spuštěné ve výchozím kontextu systémového účtu mají jiná přístupová práva k systémovému prostředku než přihlášený uživatel.
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
ms.openlocfilehash: 4ed531cb520a781fd38f8bf5491da6948901a1d5
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925732"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="7aa85-104">Postupy: Určení kontextu zabezpečení pro služby</span><span class="sxs-lookup"><span data-stu-id="7aa85-104">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="7aa85-105">Ve výchozím nastavení se služby spouštějí v jiném kontextu zabezpečení než přihlášený uživatel.</span><span class="sxs-lookup"><span data-stu-id="7aa85-105">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="7aa85-106">Služby jsou spuštěny v kontextu výchozího systémového účtu, který je volán s `LocalSystem` různými přístupovými oprávněními k systémovým prostředkům, než uživatel.</span><span class="sxs-lookup"><span data-stu-id="7aa85-106">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="7aa85-107">Toto chování můžete změnit tak, aby určovalo jiný uživatelský účet, pod kterým by měla služba běžet.</span><span class="sxs-lookup"><span data-stu-id="7aa85-107">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="7aa85-108">Kontext zabezpečení můžete nastavit tak, že budete pracovat s <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastností procesu, ve kterém je služba spuštěná.</span><span class="sxs-lookup"><span data-stu-id="7aa85-108">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="7aa85-109">Tato vlastnost umožňuje nastavit službu na jeden ze čtyř typů účtů:</span><span class="sxs-lookup"><span data-stu-id="7aa85-109">This property allows you to set the service to one of four account types:</span></span>  
  
- <span data-ttu-id="7aa85-110">`User`, což způsobí, že systém vyzve k zadání platného uživatelského jména a hesla, když je služba nainstalovaná a běží v kontextu účtu zadaného jedním uživatelem v síti.</span><span class="sxs-lookup"><span data-stu-id="7aa85-110">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
- <span data-ttu-id="7aa85-111">`LocalService`, který běží v kontextu účtu, který funguje jako Neprivilegovaný uživatel v místním počítači, a prezentuje anonymní přihlašovací údaje pro všechny vzdálené servery.</span><span class="sxs-lookup"><span data-stu-id="7aa85-111">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
- <span data-ttu-id="7aa85-112">`LocalSystem`, které běží v kontextu účtu, který poskytuje rozsáhlá místní oprávnění, a prezentuje přihlašovací údaje počítače na jakémkoli vzdáleném serveru.</span><span class="sxs-lookup"><span data-stu-id="7aa85-112">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
- <span data-ttu-id="7aa85-113">`NetworkService`, která běží v kontextu účtu, který funguje jako Neprivilegovaný uživatel v místním počítači, a prezentuje přihlašovací údaje počítače k jakémukoli vzdálenému serveru.</span><span class="sxs-lookup"><span data-stu-id="7aa85-113">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="7aa85-114">Další informace najdete v tématu <xref:System.ServiceProcess.ServiceAccount> výčet.</span><span class="sxs-lookup"><span data-stu-id="7aa85-114">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="7aa85-115">Určení kontextu zabezpečení pro službu</span><span class="sxs-lookup"><span data-stu-id="7aa85-115">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="7aa85-116">Po vytvoření služby přidejte pro ni potřebné instalační programy.</span><span class="sxs-lookup"><span data-stu-id="7aa85-116">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="7aa85-117">Další informace najdete v tématu [Postup: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="7aa85-117">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="7aa85-118">V Návrháři přejděte ke `ProjectInstaller` třídě a klikněte na instalační program procesu služby pro službu, se kterou pracujete.</span><span class="sxs-lookup"><span data-stu-id="7aa85-118">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7aa85-119">Pro každou aplikaci služby je ve třídě k dispozici alespoň dvě součásti instalace `ProjectInstaller` – jeden, který nainstaluje procesy pro všechny služby v projektu, a jeden instalační program pro každou službu, kterou aplikace obsahuje.</span><span class="sxs-lookup"><span data-stu-id="7aa85-119">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="7aa85-120">V této instanci chcete vybrat <xref:System.ServiceProcess.ServiceProcessInstaller> .</span><span class="sxs-lookup"><span data-stu-id="7aa85-120">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="7aa85-121">V okně **vlastnosti** nastavte na <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7aa85-121">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aa85-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="7aa85-122">See also</span></span>

- [<span data-ttu-id="7aa85-123">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="7aa85-123">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="7aa85-124">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="7aa85-124">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="7aa85-125">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="7aa85-125">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
