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
ms.openlocfilehash: d8cfae2fb47876d578c51e5f4acdfe0c31e752fe
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460902"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="cfa41-102">Postupy: Konfigurace aplikace Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby</span><span class="sxs-lookup"><span data-stu-id="cfa41-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
<span data-ttu-id="cfa41-103">Aplikace prohlížeče XAML (XBAP) se spouštějí v izolovaném prostoru zabezpečení s částečnou důvěryhodností, který je omezený na sadu oprávnění pro internetovou zónu.</span><span class="sxs-lookup"><span data-stu-id="cfa41-103">XAML browser applications (XBAPs) run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="cfa41-104">Tato sada oprávnění omezuje volání webové služby pouze na webové služby, které jsou umístěny v lokalitě aplikace XBAP o původu.</span><span class="sxs-lookup"><span data-stu-id="cfa41-104">This permission set restricts Web service calls to only Web services that are located at the XBAP application's site of origin.</span></span> <span data-ttu-id="cfa41-105">Když je aplikace XBAP Laděna ze sady Visual Studio 2005, ale není považována za stejnou lokalitu jako webová služba, na kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="cfa41-105">When an XBAP is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="cfa41-106">To způsobí, že výjimky zabezpečení budou vyvolány, když se XBAP pokusí zavolat webovou službu.</span><span class="sxs-lookup"><span data-stu-id="cfa41-106">This causes security exceptions to be raised when the XBAP attempts to call the Web service.</span></span> <span data-ttu-id="cfa41-107">Projekt aplikace Visual Studio 2005 XAML (WPF) se však dá nakonfigurovat tak, aby simuloval se stejným webem jako s webovou službou, kterou volá při ladění.</span><span class="sxs-lookup"><span data-stu-id="cfa41-107">However, a Visual Studio 2005 XAML Browser Application (WPF) project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="cfa41-108">To umožňuje, aby XBAP bezpečně volala webovou službu, aniž by docházelo k výjimkám zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cfa41-108">This allows the XBAP to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="cfa41-109">Konfigurování sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cfa41-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="cfa41-110">Konfigurace sady Visual Studio 2005 pro ladění XBAP, která volá webovou službu:</span><span class="sxs-lookup"><span data-stu-id="cfa41-110">To configure Visual Studio 2005 to debug an XBAP that calls a Web service:</span></span>

1. <span data-ttu-id="cfa41-111">S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="cfa41-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="cfa41-112">V **Návrháři projektu**klikněte na kartu **ladění** .</span><span class="sxs-lookup"><span data-stu-id="cfa41-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="cfa41-113">V části **spouštěcí akce** vyberte **spustit externí program** a zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="cfa41-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="cfa41-114">V části **Možnosti spuštění** zadejte do textového pole **argumenty příkazového řádku** následující text:</span><span class="sxs-lookup"><span data-stu-id="cfa41-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="cfa41-115">`-debug`  *název_souboru*</span><span class="sxs-lookup"><span data-stu-id="cfa41-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="cfa41-116">Hodnota *filename* pro parametr **-Debug** je název souboru. XBAP; například:</span><span class="sxs-lookup"><span data-stu-id="cfa41-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
> <span data-ttu-id="cfa41-117">Toto je výchozí konfigurace pro řešení vytvořená pomocí šablony projektu aplikace Visual Studio 2005 XAML (WPF).</span><span class="sxs-lookup"><span data-stu-id="cfa41-117">This is the default configuration for solutions that are created with the Visual Studio 2005 XAML Browser Application (WPF) project template.</span></span>

1. <span data-ttu-id="cfa41-118">S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="cfa41-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="cfa41-119">V **Návrháři projektu**klikněte na kartu **ladění** .</span><span class="sxs-lookup"><span data-stu-id="cfa41-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="cfa41-120">V části **Možnosti spuštění** přidejte do textového pole **argumenty příkazového** řádku následující parametr příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="cfa41-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="cfa41-121">`-debugSecurityZoneURL`  *Adresa URL*</span><span class="sxs-lookup"><span data-stu-id="cfa41-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="cfa41-122">Hodnota *URL* pro parametr **-debugSecurityZoneURL** je adresa URL pro umístění, které chcete simulovat jako web počátku aplikace.</span><span class="sxs-lookup"><span data-stu-id="cfa41-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the URL for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="cfa41-123">Zvažte například aplikaci prohlížeče XAML (XBAP), která používá webovou službu s následující adresou URL:</span><span class="sxs-lookup"><span data-stu-id="cfa41-123">As an example, consider a XAML browser application (XBAP) that uses a Web service with the following URL:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="cfa41-124">Adresa URL místa původu této webové služby je:</span><span class="sxs-lookup"><span data-stu-id="cfa41-124">The site of origin URL for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="cfa41-125">V důsledku toho parametr a hodnota příkazového řádku Complete **-debugSecurityZoneURL** je:</span><span class="sxs-lookup"><span data-stu-id="cfa41-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="cfa41-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfa41-126">See also</span></span>

- [<span data-ttu-id="cfa41-127">Hostitel WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="cfa41-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
