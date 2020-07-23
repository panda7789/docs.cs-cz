---
title: Vývoj aplikací spouštěných jako služby systému Windows
description: Viz odkazy na články, které vysvětlují, jak vyvíjet aplikace služby pro Windows pomocí sady Visual Studio nebo sady .NET SDK.
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
ms.openlocfilehash: ed02d523c21c51df2ed886843fdb71c075c93c30
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925693"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="35863-103">Vývoj aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="35863-103">Develop Windows service apps</span></span>

<span data-ttu-id="35863-104">Pomocí sady Visual Studio nebo sady .NET Framework SDK můžete snadno vytvářet služby vytvořením aplikace, která je nainstalovaná jako služba.</span><span class="sxs-lookup"><span data-stu-id="35863-104">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="35863-105">Tento typ aplikace se nazývá služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="35863-105">This type of application is called a Windows service.</span></span> <span data-ttu-id="35863-106">S funkcemi architektury můžete vytvářet služby, instalovat je a spouštět, zastavovat a jinak řídit jejich chování.</span><span class="sxs-lookup"><span data-stu-id="35863-106">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="35863-107">V aplikaci Visual Studio můžete vytvořit službu ve spravovaném kódu v jazyce Visual C# nebo Visual Basic, která může v případě potřeby spolupracovat s existujícím kódem jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="35863-107">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="35863-108">Nebo můžete vytvořit službu systému Windows v nativním jazyce C++ pomocí [Průvodce projektem ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="35863-108">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="35863-109">V této části</span><span class="sxs-lookup"><span data-stu-id="35863-109">In this section</span></span>

[<span data-ttu-id="35863-110">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="35863-110">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="35863-111">Poskytuje přehled aplikací služby systému Windows, životnosti služby a způsobu, jakým se aplikace služby liší od jiných běžných typů projektů.</span><span class="sxs-lookup"><span data-stu-id="35863-111">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="35863-112">Návod: Vytvoření aplikace služby systému Windows v návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="35863-112">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="35863-113">Poskytuje příklad vytvoření služby v Visual Basic a Visual C#.</span><span class="sxs-lookup"><span data-stu-id="35863-113">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="35863-114">Architektura programování aplikace služby</span><span class="sxs-lookup"><span data-stu-id="35863-114">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="35863-115">Vysvětluje prvky jazyka používané při programování služeb.</span><span class="sxs-lookup"><span data-stu-id="35863-115">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="35863-116">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="35863-116">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="35863-117">Popisuje proces vytváření a konfigurace služeb systému Windows pomocí šablony projektu služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="35863-117">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="35863-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="35863-118">Related sections</span></span>

<span data-ttu-id="35863-119"><xref:System.ServiceProcess.ServiceBase>– Popisuje hlavní funkce <xref:System.ServiceProcess.ServiceBase> třídy, které slouží k vytváření služeb.</span><span class="sxs-lookup"><span data-stu-id="35863-119"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="35863-120"><xref:System.ServiceProcess.ServiceProcessInstaller>– Popisuje funkce <xref:System.ServiceProcess.ServiceProcessInstaller> třídy, které se používají spolu s <xref:System.ServiceProcess.ServiceInstaller> třídou pro instalaci a odinstalaci služeb.</span><span class="sxs-lookup"><span data-stu-id="35863-120"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="35863-121"><xref:System.ServiceProcess.ServiceInstaller>– Popisuje funkce <xref:System.ServiceProcess.ServiceInstaller> třídy, která se používá společně s <xref:System.ServiceProcess.ServiceProcessInstaller> třídou pro instalaci a odinstalaci vaší služby.</span><span class="sxs-lookup"><span data-stu-id="35863-121"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="35863-122">[Vytváření projektů z šablon](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) – popisuje typy projektů používané v této kapitole a jejich výběr.</span><span class="sxs-lookup"><span data-stu-id="35863-122">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
