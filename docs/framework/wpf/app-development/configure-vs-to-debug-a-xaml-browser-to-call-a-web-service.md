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
ms.openlocfilehash: 948a730185650cb3449202503a049e9caff7c4bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547496"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="7df40-102">Postupy: Konfigurace aplikace Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby</span><span class="sxs-lookup"><span data-stu-id="7df40-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]<span data-ttu-id="7df40-103"> Spusťte v rámci částečným vztahem důvěryhodnosti zabezpečení izolovaného prostoru, který je omezen na sadu oprávnění pro zónu Internetu.</span><span class="sxs-lookup"><span data-stu-id="7df40-103"> run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="7df40-104">Omezuje volání webové služby k jenom webové služby, které jsou umístěné v této sadě oprávnění [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] serveru aplikace původu.</span><span class="sxs-lookup"><span data-stu-id="7df40-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="7df40-105">Když [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je ladit z [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], i když není to považováno za tak, aby měl stejné lokalitě původu jako webové služby odkazy.</span><span class="sxs-lookup"><span data-stu-id="7df40-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="7df40-106">Této výjimky zabezpečení příčiny vyvolá, když [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pokusí volání webové služby.</span><span class="sxs-lookup"><span data-stu-id="7df40-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="7df40-107">Ale [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projektu lze nakonfigurovat k simulaci s ke stejné lokalitě jako webovou službu zavolá při ladění původu.</span><span class="sxs-lookup"><span data-stu-id="7df40-107">However, a [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="7df40-108">To umožňuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpečně volat webovou službu bez způsobení výjimky zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7df40-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>  
  
## <a name="configuring-visual-studio"></a><span data-ttu-id="7df40-109">Konfigurace sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7df40-109">Configuring Visual Studio</span></span>  
 <span data-ttu-id="7df40-110">Ke konfiguraci [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] k ladění [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] webové služby, který volá:</span><span class="sxs-lookup"><span data-stu-id="7df40-110">To configure [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>  
  
1.  <span data-ttu-id="7df40-111">S projekt vybraný v **Průzkumníku řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7df40-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="7df40-112">V **Návrhář projektu**, klikněte **ladění** kartě.</span><span class="sxs-lookup"><span data-stu-id="7df40-112">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="7df40-113">V **spustit akci** vyberte **počáteční vnějšímu programu** a zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="7df40-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  <span data-ttu-id="7df40-114">V **možnosti spuštění** zadejte následující kód do **argumenty příkazového řádku** textového pole:</span><span class="sxs-lookup"><span data-stu-id="7df40-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="7df40-115">`-debug`  *Název souboru*</span><span class="sxs-lookup"><span data-stu-id="7df40-115">`-debug`  *filename*</span></span>  
  
     <span data-ttu-id="7df40-116">*Filename* hodnota **– ladění** parametr je název souboru .xbap; například:</span><span class="sxs-lookup"><span data-stu-id="7df40-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  <span data-ttu-id="7df40-117">Toto je výchozí konfiguraci pro řešení, které jsou vytvořené pomocí [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] šablona projektu.</span><span class="sxs-lookup"><span data-stu-id="7df40-117">This is the default configuration for solutions that are created with the [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>  
  
1.  <span data-ttu-id="7df40-118">S projekt vybraný v **Průzkumníku řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7df40-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="7df40-119">V **Návrhář projektu**, klikněte **ladění** kartě.</span><span class="sxs-lookup"><span data-stu-id="7df40-119">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="7df40-120">V **možnosti spuštění** přidejte následující parametr příkazového řádku k **argumenty příkazového řádku** textového pole:</span><span class="sxs-lookup"><span data-stu-id="7df40-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="7df40-121">`-debugSecurityZoneURL`  *ADRESA URL*</span><span class="sxs-lookup"><span data-stu-id="7df40-121">`-debugSecurityZoneURL`  *URL*</span></span>  
  
     <span data-ttu-id="7df40-122">*URL* hodnota **- debugSecurityZoneURL** parametr je [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] pro umístění, které chcete simulovat jako webu původu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="7df40-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>  
  
 <span data-ttu-id="7df40-123">Jako příklad, zvažte [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] používající webové služby s následující [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="7df40-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 <span data-ttu-id="7df40-124">Místo původu [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] pro tento Web je služba:</span><span class="sxs-lookup"><span data-stu-id="7df40-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>  
  
 `http://services.msdn.microsoft.com`  
  
 <span data-ttu-id="7df40-125">V důsledku toho dokončení **- debugSecurityZoneURL** parametr příkazového řádku a hodnota je:</span><span class="sxs-lookup"><span data-stu-id="7df40-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a><span data-ttu-id="7df40-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7df40-126">See Also</span></span>  
 [<span data-ttu-id="7df40-127">Hostitel WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="7df40-127">WPF Host (PresentationHost.exe)</span></span>](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
