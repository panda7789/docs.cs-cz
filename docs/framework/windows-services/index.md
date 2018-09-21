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
ms.openlocfilehash: aa5e18f7e0ee1fc0836054b692872b18678106f3
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537472"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="d5838-102">Vývoj aplikací pro službu Windows</span><span class="sxs-lookup"><span data-stu-id="d5838-102">Develop Windows service apps</span></span>

<span data-ttu-id="d5838-103">Pomocí sady Visual Studio nebo sady SDK rozhraní .NET Framework, můžete snadno vytvářet služby tak, že vytvoříte aplikaci, která je nainstalována jako služba.</span><span class="sxs-lookup"><span data-stu-id="d5838-103">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="d5838-104">Tento typ aplikace se nazývá služby Windows.</span><span class="sxs-lookup"><span data-stu-id="d5838-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="d5838-105">S funkcemi rozhraní framework můžete vytvářet služby, je, nainstalovat a spuštění, zastavení a jinak řídit jejich chování.</span><span class="sxs-lookup"><span data-stu-id="d5838-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="d5838-106">V sadě Visual Studio můžete vytvořit službu ve spravovaném kódu v jazyce Visual C# nebo Visual Basic, která můžou spolupracovat s existujícího kódu C++, pokud je to nutné.</span><span class="sxs-lookup"><span data-stu-id="d5838-106">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="d5838-107">Nebo můžete vytvořit službu Windows v nativním kódu C++ pomocí [Průvodce projektem ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="d5838-107">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d5838-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d5838-108">In this section</span></span>

[<span data-ttu-id="d5838-109">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="d5838-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)

<span data-ttu-id="d5838-110">Poskytuje přehled aplikace služby Windows, dobu života služby a jak se liší od jiné běžné typy projektů aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="d5838-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="d5838-111">Návod: Vytvoření aplikace služby systému Windows v návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="d5838-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="d5838-112">Poskytuje příklad vytvoření služby v jazyce Visual Basic a Visual C#.</span><span class="sxs-lookup"><span data-stu-id="d5838-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="d5838-113">Architektura programování aplikace služby</span><span class="sxs-lookup"><span data-stu-id="d5838-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)

<span data-ttu-id="d5838-114">Vysvětluje prvky jazyka, použít v service programování.</span><span class="sxs-lookup"><span data-stu-id="d5838-114">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="d5838-115">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="d5838-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

<span data-ttu-id="d5838-116">Popisuje postup vytvoření a konfigurace služeb Windows pomocí šablony projektu služby Windows.</span><span class="sxs-lookup"><span data-stu-id="d5838-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="d5838-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d5838-117">Related sections</span></span>

<span data-ttu-id="d5838-118"><xref:System.ServiceProcess.ServiceBase> – Popisuje hlavní funkce <xref:System.ServiceProcess.ServiceBase> třídu, která se používá k vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="d5838-118"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="d5838-119"><xref:System.ServiceProcess.ServiceProcessInstaller> – Popisuje funkce <xref:System.ServiceProcess.ServiceProcessInstaller> třídu, která se používá spolu s <xref:System.ServiceProcess.ServiceInstaller> třídy k instalaci a odinstalaci služby.</span><span class="sxs-lookup"><span data-stu-id="d5838-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="d5838-120"><xref:System.ServiceProcess.ServiceInstaller> – Popisuje funkce <xref:System.ServiceProcess.ServiceInstaller> třídu, která se používá spolu s <xref:System.ServiceProcess.ServiceProcessInstaller> třídy k instalaci a odinstalaci služby.</span><span class="sxs-lookup"><span data-stu-id="d5838-120"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="d5838-121">[Vytvářet projekty ze šablon](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2) -popisuje projekty typů použitých v této kapitole a jak si vybrat mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="d5838-121">[Create Projects from Templates](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
