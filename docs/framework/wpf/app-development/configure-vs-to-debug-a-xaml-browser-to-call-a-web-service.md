---
title: 'Postupy: Konfigurace aplikace Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: 8ec278f2bc66d9b40786123af684f6468b6a9d83
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005672"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="f0900-102">Postupy: Konfigurace aplikace Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby</span><span class="sxs-lookup"><span data-stu-id="f0900-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] <span data-ttu-id="f0900-103">běží v izolovaném prostoru zabezpečení s částečnou důvěryhodností, který je omezený na sadu oprávnění pro internetovou zónu.</span><span class="sxs-lookup"><span data-stu-id="f0900-103">run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="f0900-104">Tato sada oprávnění omezuje volání webové služby pouze na webové služby, které jsou umístěny v lokalitě aplikace [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] původu.</span><span class="sxs-lookup"><span data-stu-id="f0900-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="f0900-105">Když je [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Laděna ze sady Visual Studio 2005, nepovažuje se za stejný web jako webová služba, na kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="f0900-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="f0900-106">To způsobí, že výjimky zabezpečení budou vyvolány, když se [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pokusí zavolat webovou službu.</span><span class="sxs-lookup"><span data-stu-id="f0900-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="f0900-107">Projekt sady Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] se však dá nakonfigurovat tak, aby simuloval stejný web jako Web Service, který při ladění volá.</span><span class="sxs-lookup"><span data-stu-id="f0900-107">However, a Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="f0900-108">To umožňuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpečně volat webovou službu, aniž by došlo k výjimkám zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f0900-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="f0900-109">Konfigurování sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f0900-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="f0900-110">Konfigurace sady Visual Studio 2005 pro ladění [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], která volá webovou službu:</span><span class="sxs-lookup"><span data-stu-id="f0900-110">To configure Visual Studio 2005 to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>

1. <span data-ttu-id="f0900-111">S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f0900-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="f0900-112">V **Návrháři projektu**klikněte na kartu **ladění** .</span><span class="sxs-lookup"><span data-stu-id="f0900-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="f0900-113">V části **spouštěcí akce** vyberte **spustit externí program** a zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="f0900-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="f0900-114">V části **Možnosti spuštění** zadejte do textového pole **argumenty příkazového řádku** následující text:</span><span class="sxs-lookup"><span data-stu-id="f0900-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="f0900-115">`-debug`  *název_souboru*</span><span class="sxs-lookup"><span data-stu-id="f0900-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="f0900-116">Hodnota *filename* pro parametr **-Debug** je název souboru. XBAP; například:</span><span class="sxs-lookup"><span data-stu-id="f0900-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
> <span data-ttu-id="f0900-117">Toto je výchozí konfigurace pro řešení, která jsou vytvořena pomocí šablony projektu [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] sady Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="f0900-117">This is the default configuration for solutions that are created with the Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>

1. <span data-ttu-id="f0900-118">S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f0900-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="f0900-119">V **Návrháři projektu**klikněte na kartu **ladění** .</span><span class="sxs-lookup"><span data-stu-id="f0900-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="f0900-120">V části **Možnosti spuštění** přidejte do textového pole **argumenty příkazového** řádku následující parametr příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="f0900-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="f0900-121">`-debugSecurityZoneURL`  *Adresa URL*</span><span class="sxs-lookup"><span data-stu-id="f0900-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="f0900-122">Hodnota *URL* pro parametr **-debugSecurityZoneURL** je [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] pro umístění, které chcete simulovat jako web počátku aplikace.</span><span class="sxs-lookup"><span data-stu-id="f0900-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="f0900-123">Zvažte například [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], který používá webovou službu s následující adresou URL:</span><span class="sxs-lookup"><span data-stu-id="f0900-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following URL:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="f0900-124">Adresa URL místa původu této webové služby je:</span><span class="sxs-lookup"><span data-stu-id="f0900-124">The site of origin URL for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="f0900-125">V důsledku toho parametr a hodnota příkazového řádku Complete **-debugSecurityZoneURL** je:</span><span class="sxs-lookup"><span data-stu-id="f0900-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="f0900-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0900-126">See also</span></span>

- [<span data-ttu-id="f0900-127">Hostitel WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="f0900-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
