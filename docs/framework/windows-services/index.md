---
title: "Vývoj aplikací spouštěných jako služby systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 2912568e967c8c6096842b1b4f24eac88318dffb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="developing-windows-service-applications"></a><span data-ttu-id="db8e7-102">Vývoj aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="db8e7-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="db8e7-103">Pomocí Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] nebo Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, můžete snadno vytvořit služby tak, že vytvoříte aplikaci, která je nainstalován jako služba.</span><span class="sxs-lookup"><span data-stu-id="db8e7-103">Using Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="db8e7-104">Tento typ aplikace se nazývá služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="db8e7-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="db8e7-105">S funkcemi framework můžete vytvořit služby, je, nainstalovat a spustit, zastavit a jinak řídit jejich chování.</span><span class="sxs-lookup"><span data-stu-id="db8e7-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="db8e7-106">Šablony služeb systému Windows pro jazyk C++ nebyla obsažena v sadě Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="db8e7-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="db8e7-107">K vytvoření služby systému Windows, můžete buď vytvořit službu ve spravovaném kódu v jazyce Visual C# nebo Visual Basic, který může spolupracovat s existujícího kódu C++ v případě potřeby, nebo služby systému Windows můžete vytvořit v nativním kódu C++ pomocí [–PrůvodceprojektemknihovnyATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="db8e7-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db8e7-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="db8e7-108">In This Section</span></span>  
 [<span data-ttu-id="db8e7-109">Úvod do aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="db8e7-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="db8e7-110">Poskytuje přehled aplikace služby systému Windows, doba platnosti služby a jak aplikace služby se liší od jiných běžné typy projektů.</span><span class="sxs-lookup"><span data-stu-id="db8e7-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="db8e7-111">Návod: Vytvoření aplikace služby systému Windows v Návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="db8e7-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="db8e7-112">Poskytuje příklad vytvoření služby v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] a Visual C#.</span><span class="sxs-lookup"><span data-stu-id="db8e7-112">Provides an example of creating a service in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] and Visual C#.</span></span>  
  
 [<span data-ttu-id="db8e7-113">Architektura programování aplikace služby</span><span class="sxs-lookup"><span data-stu-id="db8e7-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="db8e7-114">Vysvětluje prvky jazyka, používané v programování služby.</span><span class="sxs-lookup"><span data-stu-id="db8e7-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="db8e7-115">Postupy: vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="db8e7-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="db8e7-116">Popisuje postup vytvoření a konfigurace služby systému Windows pomocí šablony projektu služeb systému Windows.</span><span class="sxs-lookup"><span data-stu-id="db8e7-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="db8e7-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="db8e7-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="db8e7-118">Popisuje hlavní funkce <xref:System.ServiceProcess.ServiceBase> třídy, která se používá k vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="db8e7-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="db8e7-119">Popisuje funkce <xref:System.ServiceProcess.ServiceProcessInstaller> třídy, která se používá spolu s <xref:System.ServiceProcess.ServiceInstaller> třída k instalaci a odinstalaci vašich služeb.</span><span class="sxs-lookup"><span data-stu-id="db8e7-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="db8e7-120">Popisuje funkce <xref:System.ServiceProcess.ServiceInstaller> třídy, která se používá spolu s <xref:System.ServiceProcess.ServiceProcessInstaller> třída k instalaci a odinstalaci služby.</span><span class="sxs-lookup"><span data-stu-id="db8e7-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 [<span data-ttu-id="db8e7-121">NIB vytváření projektů ze šablon</span><span class="sxs-lookup"><span data-stu-id="db8e7-121">NIB Creating Projects from Templates</span></span>](http://msdn.microsoft.com/en-us/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 <span data-ttu-id="db8e7-122">Popisuje projektů typy používané v této kapitoly a jak vybrat mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="db8e7-122">Describes the projects types used in this chapter and how to choose between them.</span></span>
