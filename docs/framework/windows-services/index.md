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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053545"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="804a3-102">Vývoj aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="804a3-102">Develop Windows service apps</span></span>

<span data-ttu-id="804a3-103">Pomocí sady Visual Studio nebo sady .NET Framework SDK můžete snadno vytvářet služby vytvořením aplikace, která je nainstalovaná jako služba.</span><span class="sxs-lookup"><span data-stu-id="804a3-103">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="804a3-104">Tento typ aplikace se nazývá služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="804a3-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="804a3-105">S funkcemi architektury můžete vytvářet služby, instalovat je a spouštět, zastavovat a jinak řídit jejich chování.</span><span class="sxs-lookup"><span data-stu-id="804a3-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="804a3-106">V aplikaci Visual Studio můžete vytvořit službu ve spravovaném kódu v jazyce C# Visual nebo Visual Basic, která může v případě potřeby C++ spolupracovat s existujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="804a3-106">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="804a3-107">Nebo můžete vytvořit službu systému Windows v nativním režimu C++ pomocí [Průvodce projektem ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="804a3-107">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="804a3-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="804a3-108">In this section</span></span>

[<span data-ttu-id="804a3-109">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="804a3-109">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="804a3-110">Poskytuje přehled aplikací služby systému Windows, životnosti služby a způsobu, jakým se aplikace služby liší od jiných běžných typů projektů.</span><span class="sxs-lookup"><span data-stu-id="804a3-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="804a3-111">Návod: Vytvoření aplikace služby systému Windows v Návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="804a3-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="804a3-112">V této části najdete příklad vytvoření služby v Visual Basic a vizuálu C#.</span><span class="sxs-lookup"><span data-stu-id="804a3-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="804a3-113">Architektura programování aplikace služby</span><span class="sxs-lookup"><span data-stu-id="804a3-113">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="804a3-114">Vysvětluje prvky jazyka používané při programování služeb.</span><span class="sxs-lookup"><span data-stu-id="804a3-114">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="804a3-115">Postupy: Vytvořit služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="804a3-115">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="804a3-116">Popisuje proces vytváření a konfigurace služeb systému Windows pomocí šablony projektu služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="804a3-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="804a3-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="804a3-117">Related sections</span></span>

<span data-ttu-id="804a3-118"><xref:System.ServiceProcess.ServiceBase>– Popisuje hlavní funkce <xref:System.ServiceProcess.ServiceBase> třídy, které slouží k vytváření služeb.</span><span class="sxs-lookup"><span data-stu-id="804a3-118"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="804a3-119"><xref:System.ServiceProcess.ServiceProcessInstaller>– Popisuje funkce <xref:System.ServiceProcess.ServiceProcessInstaller> třídy, které se používají spolu <xref:System.ServiceProcess.ServiceInstaller> s třídou pro instalaci a odinstalaci služeb.</span><span class="sxs-lookup"><span data-stu-id="804a3-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="804a3-120"><xref:System.ServiceProcess.ServiceInstaller>– Popisuje funkce <xref:System.ServiceProcess.ServiceInstaller> třídy, která se používá společně <xref:System.ServiceProcess.ServiceProcessInstaller> s třídou pro instalaci a odinstalaci vaší služby.</span><span class="sxs-lookup"><span data-stu-id="804a3-120"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="804a3-121">[Vytváření projektů z šablon](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) – popisuje typy projektů používané v této kapitole a jejich výběr.</span><span class="sxs-lookup"><span data-stu-id="804a3-121">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
