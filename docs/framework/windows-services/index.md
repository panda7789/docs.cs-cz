---
title: Vývoj aplikací spouštěných jako služby systému Windows
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
manager: douge
ms.openlocfilehash: 2c7fb148b96d5ff9804bcb0bb7c842c475c0f117
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740827"
---
# <a name="developing-windows-service-applications"></a><span data-ttu-id="cc962-102">Vývoj aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="cc962-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="cc962-103">Pomocí sady Microsoft Visual Studio nebo službou Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, můžete snadno vytvářet služby tak, že vytvoříte aplikaci, která je nainstalována jako služba.</span><span class="sxs-lookup"><span data-stu-id="cc962-103">Using Microsoft Visual Studio or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="cc962-104">Tento typ aplikace se nazývá služby Windows.</span><span class="sxs-lookup"><span data-stu-id="cc962-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="cc962-105">S funkcemi rozhraní framework můžete vytvářet služby, je, nainstalovat a spuštění, zastavení a jinak řídit jejich chování.</span><span class="sxs-lookup"><span data-stu-id="cc962-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="cc962-106">Šablona služby Windows pro jazyk C++ nebyla zahrnuta v sadě Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="cc962-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="cc962-107">Pokud chcete vytvořit službu Windows, služby můžete vytvořit buď ve spravovaném kódu v jazyce Visual C# nebo Visual Basic, který může spolupracovat s existujícího kódu C++, pokud je to nutné, nebo můžete vytvořit službu Windows v nativním kódu C++ pomocí [Průvodce projektem ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="cc962-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc962-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cc962-108">In This Section</span></span>  
 [<span data-ttu-id="cc962-109">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="cc962-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="cc962-110">Poskytuje přehled aplikace služby Windows, dobu života služby a jak se liší od jiné běžné typy projektů aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="cc962-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="cc962-111">Návod: Vytvoření aplikace služby systému Windows v návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="cc962-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="cc962-112">Poskytuje příklad vytvoření služby v jazyce Visual Basic a Visual C#.</span><span class="sxs-lookup"><span data-stu-id="cc962-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>  
  
 [<span data-ttu-id="cc962-113">Architektura programování aplikace služby</span><span class="sxs-lookup"><span data-stu-id="cc962-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="cc962-114">Vysvětluje prvky jazyka, použít v service programování.</span><span class="sxs-lookup"><span data-stu-id="cc962-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="cc962-115">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="cc962-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="cc962-116">Popisuje postup vytvoření a konfigurace služeb Windows pomocí šablony projektu služby Windows.</span><span class="sxs-lookup"><span data-stu-id="cc962-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cc962-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cc962-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="cc962-118">Popisuje hlavní funkce <xref:System.ServiceProcess.ServiceBase> třídu, která se používá k vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="cc962-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="cc962-119">Popisuje funkce <xref:System.ServiceProcess.ServiceProcessInstaller> třídu, která se používá spolu s <xref:System.ServiceProcess.ServiceInstaller> třídy k instalaci a odinstalaci služby.</span><span class="sxs-lookup"><span data-stu-id="cc962-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="cc962-120">Popisuje funkce <xref:System.ServiceProcess.ServiceInstaller> třídu, která se používá spolu s <xref:System.ServiceProcess.ServiceProcessInstaller> třídy k instalaci a odinstalaci služby.</span><span class="sxs-lookup"><span data-stu-id="cc962-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 [<span data-ttu-id="cc962-121">NIB vytváření projektů ze šablon</span><span class="sxs-lookup"><span data-stu-id="cc962-121">NIB Creating Projects from Templates</span></span>](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 <span data-ttu-id="cc962-122">Popisuje projekty typů použitých v této kapitole a jak si vybrat mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="cc962-122">Describes the projects types used in this chapter and how to choose between them.</span></span>
