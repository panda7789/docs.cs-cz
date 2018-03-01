---
title: "Nasazení aplikací odkazujících na ovládací prvky Power Pack (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a9562acf05cd27eed7bc1ad963845af9a7ca5f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a><span data-ttu-id="74ef2-102">Nasazení aplikací odkazujících na ovládací prvky Power Pack (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="74ef2-102">Deploying applications that reference Power Packs controls (Visual Studio)</span></span>
<span data-ttu-id="74ef2-103">Pokud chcete nasadit aplikaci, která odkazuje na ovládací prvky Power Pack (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, nebo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), ovládací prvky, musí být nainstalován v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="74ef2-103">If you want to deploy an application that references the Power Packs controls (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), the controls must be installed on the destination computer.</span></span>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a><span data-ttu-id="74ef2-104">Instalace ovládací prvky Power Pack jako předpoklad</span><span class="sxs-lookup"><span data-stu-id="74ef2-104">Installing the Power Packs controls as a prerequisite</span></span>  
 <span data-ttu-id="74ef2-105">Pokud chcete úspěšně nasadit aplikaci, musíte také nasadit všechny součásti, které jsou odkazovány pomocí aplikace.</span><span class="sxs-lookup"><span data-stu-id="74ef2-105">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="74ef2-106">Proces instalace požadovaných součástí se označuje jako *zavádění*.</span><span class="sxs-lookup"><span data-stu-id="74ef2-106">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="74ef2-107">Když [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] je nainstalován ve svém vývojovém počítači, Power Pack balíček zaváděcího nástroje je přidán do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] adresáře zaváděcího nástroje.</span><span class="sxs-lookup"><span data-stu-id="74ef2-107">When [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] is installed on your development computer, a Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bootstrapper directory.</span></span> <span data-ttu-id="74ef2-108">Tento balíček je k dispozici v případě postupujte podle pokynů pro přidání předpokladů pro buď [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] nebo instalační služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="74ef2-108">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="74ef2-109">Ve výchozím nastavení jsou zaváděné součásti nasazeny ze stejného umístění jako instalační balíček.</span><span class="sxs-lookup"><span data-stu-id="74ef2-109">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="74ef2-110">Alternativně můžete nainstalovat komponenty z adresy URL nebo sdíleného umístění, ze kterého mohou uživatelé stáhnout je podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="74ef2-110">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74ef2-111">K instalaci samozaváděcí komponenty, může uživatel potřebovat oprávnění pro správu nebo podobné uživatele v počítači.</span><span class="sxs-lookup"><span data-stu-id="74ef2-111">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="74ef2-112">Pro [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikace, to znamená, že bude uživatel potřebovat oprávnění správce k instalaci aplikace, bez ohledu na úroveň zabezpečení, který je určený aplikací.</span><span class="sxs-lookup"><span data-stu-id="74ef2-112">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="74ef2-113">Po instalaci aplikace, může uživatel spustit aplikaci bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="74ef2-113">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="74ef2-114">Během instalace uživatelům se zobrazí výzva k instalaci ovládací prvky Power Pack, pokud se nenachází v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="74ef2-114">During installation, users will be prompted to install the Power Packs controls if they are not present on the destination computer.</span></span>  
  
 <span data-ttu-id="74ef2-115">Jako alternativu k zavedení spouštěcího programu můžete předem nasadit ovládací prvky Power Pack pomocí systém distribuce elektronické softwaru jako je například Microsoft Systems Management Server.</span><span class="sxs-lookup"><span data-stu-id="74ef2-115">As an alternative to bootstrapping, you can pre-deploy the Power Packs controls by using an electronic software distribution system such as Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ef2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="74ef2-116">See also</span></span>  
 [<span data-ttu-id="74ef2-117">Postupy: instalace předpokladů s aplikací ClickOnce</span><span class="sxs-lookup"><span data-stu-id="74ef2-117">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="74ef2-118">Ovládací prvky Power Pack jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="74ef2-118">Visual Basic Power Packs Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
