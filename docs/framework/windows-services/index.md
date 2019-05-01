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
ms.openlocfilehash: 32aa2c1c4cd31e4591c9fa30c05ebe61058f94c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008704"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="4bf38-102">Vývoj aplikací pro službu Windows</span><span class="sxs-lookup"><span data-stu-id="4bf38-102">Develop Windows service apps</span></span>

<span data-ttu-id="4bf38-103">Pomocí sady Visual Studio nebo sady SDK rozhraní .NET Framework, můžete snadno vytvářet služby tak, že vytvoříte aplikaci, která je nainstalována jako služba.</span><span class="sxs-lookup"><span data-stu-id="4bf38-103">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="4bf38-104">Tento typ aplikace se nazývá služby Windows.</span><span class="sxs-lookup"><span data-stu-id="4bf38-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="4bf38-105">S funkcemi rozhraní framework můžete vytvářet služby, je, nainstalovat a spuštění, zastavení a jinak řídit jejich chování.</span><span class="sxs-lookup"><span data-stu-id="4bf38-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="4bf38-106">V sadě Visual Studio můžete vytvořit službu ve spravovaném kódu v jazyce Visual C# nebo Visual Basic, která můžou spolupracovat s existujícího kódu C++, pokud je to nutné.</span><span class="sxs-lookup"><span data-stu-id="4bf38-106">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="4bf38-107">Nebo můžete vytvořit službu Windows v nativním kódu C++ pomocí [Průvodce projektem ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="4bf38-107">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4bf38-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4bf38-108">In this section</span></span>

[<span data-ttu-id="4bf38-109">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="4bf38-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)

<span data-ttu-id="4bf38-110">Poskytuje přehled aplikace služby Windows, dobu života služby a jak se liší od jiné běžné typy projektů aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="4bf38-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="4bf38-111">Návod: Vytvoření aplikace služby Windows v Návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="4bf38-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="4bf38-112">Poskytuje příklad vytvoření služby v jazyce Visual Basic a Visual C#.</span><span class="sxs-lookup"><span data-stu-id="4bf38-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="4bf38-113">Architektura programování aplikace služby</span><span class="sxs-lookup"><span data-stu-id="4bf38-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)

<span data-ttu-id="4bf38-114">Vysvětluje prvky jazyka, použít v service programování.</span><span class="sxs-lookup"><span data-stu-id="4bf38-114">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="4bf38-115">Postupy: Vytvoření služeb Windows</span><span class="sxs-lookup"><span data-stu-id="4bf38-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

<span data-ttu-id="4bf38-116">Popisuje postup vytvoření a konfigurace služeb Windows pomocí šablony projektu služby Windows.</span><span class="sxs-lookup"><span data-stu-id="4bf38-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="4bf38-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4bf38-117">Related sections</span></span>

<span data-ttu-id="4bf38-118"><xref:System.ServiceProcess.ServiceBase> – Popisuje hlavní funkce <xref:System.ServiceProcess.ServiceBase> třídu, která se používá k vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="4bf38-118"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="4bf38-119"><xref:System.ServiceProcess.ServiceProcessInstaller> – Popisuje funkce <xref:System.ServiceProcess.ServiceProcessInstaller> třídu, která se používá spolu s <xref:System.ServiceProcess.ServiceInstaller> třídy k instalaci a odinstalaci služby.</span><span class="sxs-lookup"><span data-stu-id="4bf38-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="4bf38-120"><xref:System.ServiceProcess.ServiceInstaller> – Popisuje funkce <xref:System.ServiceProcess.ServiceInstaller> třídu, která se používá spolu s <xref:System.ServiceProcess.ServiceProcessInstaller> třídy k instalaci a odinstalaci služby.</span><span class="sxs-lookup"><span data-stu-id="4bf38-120"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="4bf38-121">[Vytvářet projekty ze šablon](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -popisuje projekty typů použitých v této kapitole a jak si vybrat mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="4bf38-121">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
