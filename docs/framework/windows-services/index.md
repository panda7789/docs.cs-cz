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
ms.openlocfilehash: 61f969c22ac06bd6ed20ccfa9124db3bb35d0692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71053545"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="6fd1d-102">Vývoj servisních aplikací pro Windows</span><span class="sxs-lookup"><span data-stu-id="6fd1d-102">Develop Windows service apps</span></span>

<span data-ttu-id="6fd1d-103">Pomocí sady Visual Studio nebo sady .NET Framework SDK můžete snadno vytvářet služby vytvořením aplikace, která je nainstalována jako služba.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-103">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="6fd1d-104">Tento typ aplikace se nazývá služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="6fd1d-105">Pomocí funkcí architektury můžete vytvářet služby, instalovat je a spouštět, zastavovat a jinak řídit jejich chování.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="6fd1d-106">V sadě Visual Studio můžete vytvořit službu ve spravovaném kódu v jazyce Visual C# nebo Visual Basic, který může v případě potřeby spolupracovat s existujícím kódem jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-106">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="6fd1d-107">Nebo můžete vytvořit službu systému Windows v nativním jazyce C++ pomocí [Průvodce projektem ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="6fd1d-107">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6fd1d-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6fd1d-108">In this section</span></span>

[<span data-ttu-id="6fd1d-109">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="6fd1d-109">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="6fd1d-110">Poskytuje přehled aplikací služeb systému Windows, životnost služby a způsob, jakým se aplikace služby liší od jiných běžných typů projektů.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="6fd1d-111">Návod: Vytvoření aplikace služby systému Windows v návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="6fd1d-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="6fd1d-112">Obsahuje příklad vytvoření služby v jazyce Visual Basic a Visual C#.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="6fd1d-113">Architektura programování aplikace služby</span><span class="sxs-lookup"><span data-stu-id="6fd1d-113">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="6fd1d-114">Vysvětluje jazykové prvky používané v programování služeb.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-114">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="6fd1d-115">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="6fd1d-115">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="6fd1d-116">Popisuje proces vytváření a konfigurace služeb systému Windows pomocí šablony projektu služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="6fd1d-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6fd1d-117">Related sections</span></span>

<span data-ttu-id="6fd1d-118"><xref:System.ServiceProcess.ServiceBase>- Popisuje hlavní rysy <xref:System.ServiceProcess.ServiceBase> třídy, která se používá k vytváření služeb.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-118"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="6fd1d-119"><xref:System.ServiceProcess.ServiceProcessInstaller>- Popisuje funkce <xref:System.ServiceProcess.ServiceProcessInstaller> třídy, která se používá <xref:System.ServiceProcess.ServiceInstaller> spolu s třídou k instalaci a odinstalaci služeb.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="6fd1d-120"><xref:System.ServiceProcess.ServiceInstaller>- Popisuje funkce <xref:System.ServiceProcess.ServiceInstaller> třídy, která se používá <xref:System.ServiceProcess.ServiceProcessInstaller> spolu s třídou k instalaci a odinstalaci služby.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-120"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="6fd1d-121">[Vytvořit projekty ze šablon](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) - Popisuje typy projektů použité v této kapitole a způsob jejich výběru.</span><span class="sxs-lookup"><span data-stu-id="6fd1d-121">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
