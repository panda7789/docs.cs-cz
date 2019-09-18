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
ms.openlocfilehash: dd2a9c4485e151d4cb1c9d5ae3a95a69fcc416d4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053583"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="ee416-102">Postupy: Určení kontextu zabezpečení pro služby</span><span class="sxs-lookup"><span data-stu-id="ee416-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="ee416-103">Ve výchozím nastavení se služby spouštějí v jiném kontextu zabezpečení než přihlášený uživatel.</span><span class="sxs-lookup"><span data-stu-id="ee416-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="ee416-104">Služby jsou spuštěny v kontextu výchozího systémového účtu, který je `LocalSystem`volán s různými přístupovými oprávněními k systémovým prostředkům, než uživatel.</span><span class="sxs-lookup"><span data-stu-id="ee416-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="ee416-105">Toto chování můžete změnit tak, aby určovalo jiný uživatelský účet, pod kterým by měla služba běžet.</span><span class="sxs-lookup"><span data-stu-id="ee416-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="ee416-106">Kontext zabezpečení můžete nastavit tak, že budete pracovat <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> s vlastností procesu, ve kterém je služba spuštěná.</span><span class="sxs-lookup"><span data-stu-id="ee416-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="ee416-107">Tato vlastnost umožňuje nastavit službu na jeden ze čtyř typů účtů:</span><span class="sxs-lookup"><span data-stu-id="ee416-107">This property allows you to set the service to one of four account types:</span></span>  
  
- <span data-ttu-id="ee416-108">`User`, což způsobí, že systém vyzve k zadání platného uživatelského jména a hesla, když je služba nainstalovaná a běží v kontextu účtu zadaného jedním uživatelem v síti.</span><span class="sxs-lookup"><span data-stu-id="ee416-108">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
- <span data-ttu-id="ee416-109">`LocalService`, který běží v kontextu účtu, který funguje jako Neprivilegovaný uživatel v místním počítači, a prezentuje anonymní přihlašovací údaje pro všechny vzdálené servery.</span><span class="sxs-lookup"><span data-stu-id="ee416-109">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
- <span data-ttu-id="ee416-110">`LocalSystem`, které běží v kontextu účtu, který poskytuje rozsáhlá místní oprávnění, a prezentuje přihlašovací údaje počítače na jakémkoli vzdáleném serveru.</span><span class="sxs-lookup"><span data-stu-id="ee416-110">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
- <span data-ttu-id="ee416-111">`NetworkService`, která běží v kontextu účtu, který funguje jako Neprivilegovaný uživatel v místním počítači, a prezentuje přihlašovací údaje počítače k jakémukoli vzdálenému serveru.</span><span class="sxs-lookup"><span data-stu-id="ee416-111">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="ee416-112">Další informace najdete v tématu <xref:System.ServiceProcess.ServiceAccount> výčet.</span><span class="sxs-lookup"><span data-stu-id="ee416-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="ee416-113">Určení kontextu zabezpečení pro službu</span><span class="sxs-lookup"><span data-stu-id="ee416-113">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="ee416-114">Po vytvoření služby přidejte pro ni potřebné instalační programy.</span><span class="sxs-lookup"><span data-stu-id="ee416-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="ee416-115">Další informace najdete v tématu [jak: Přidejte instalační programy do aplikace](how-to-add-installers-to-your-service-application.md)služby.</span><span class="sxs-lookup"><span data-stu-id="ee416-115">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="ee416-116">V Návrháři přejděte ke `ProjectInstaller` třídě a klikněte na instalační program procesu služby pro službu, se kterou pracujete.</span><span class="sxs-lookup"><span data-stu-id="ee416-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ee416-117">Pro každou aplikaci služby je ve `ProjectInstaller` třídě k dispozici alespoň dvě součásti instalace – jeden, který nainstaluje procesy pro všechny služby v projektu, a jeden instalační program pro každou službu, kterou aplikace obsahuje.</span><span class="sxs-lookup"><span data-stu-id="ee416-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="ee416-118">V této instanci chcete vybrat <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="ee416-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="ee416-119">V okně **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ee416-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee416-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee416-120">See also</span></span>

- [<span data-ttu-id="ee416-121">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="ee416-121">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="ee416-122">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="ee416-122">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="ee416-123">Postupy: Vytvořit služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="ee416-123">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
