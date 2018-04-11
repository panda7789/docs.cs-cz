---
title: Nasazení aplikací odkazujících na součást PrintForm (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 15b6e21e769c90e23e66e4f87b37f74462423985
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a><span data-ttu-id="2c41e-102">Nasazení aplikací odkazujících na součást PrintForm (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c41e-102">Deploying applications that reference the PrintForm component (Visual Basic)</span></span>
<span data-ttu-id="2c41e-103">Pokud chcete nasadit aplikaci, která odkazuje <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti, součásti musí být nainstalován v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="2c41e-103">If you want to deploy an application that references the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component, the component must be installed on the destination computer.</span></span>  
  
 <span data-ttu-id="2c41e-104">Ovládací prvky PowerPack jsou již zahrnuty v sadě Visual Studio, ale si můžete stáhnout z [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="2c41e-104">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="installing-the-printform-as-a-prerequisite"></a><span data-ttu-id="2c41e-105">Předpokladem je instalace PrintForm</span><span class="sxs-lookup"><span data-stu-id="2c41e-105">Installing the PrintForm as a prerequisite</span></span>  
 <span data-ttu-id="2c41e-106">Pokud chcete úspěšně nasadit aplikaci, musíte také nasadit všechny součásti, které jsou odkazovány pomocí aplikace.</span><span class="sxs-lookup"><span data-stu-id="2c41e-106">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="2c41e-107">Proces instalace požadovaných součástí se označuje jako *zavádění*.</span><span class="sxs-lookup"><span data-stu-id="2c41e-107">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="2c41e-108">Když <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> ve svém vývojovém počítači je nainstalována součást, balíček zaváděcího nástroje sady Microsoft Visual Basic Power Pack se přidá do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] adresáře zaváděcího nástroje.</span><span class="sxs-lookup"><span data-stu-id="2c41e-108">When the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is installed on your development computer, a Microsoft Visual Basic Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bootstrapper directory.</span></span> <span data-ttu-id="2c41e-109">Tento balíček je k dispozici v případě postupujte podle pokynů pro přidání předpokladů pro buď [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] nebo instalační služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2c41e-109">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="2c41e-110">Ve výchozím nastavení jsou zaváděné součásti nasazeny ze stejného umístění jako instalační balíček.</span><span class="sxs-lookup"><span data-stu-id="2c41e-110">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="2c41e-111">Alternativně můžete nainstalovat komponenty z adresy URL nebo sdíleného umístění, ze kterého mohou uživatelé stáhnout je podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="2c41e-111">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c41e-112">K instalaci samozaváděcí komponenty, může uživatel potřebovat oprávnění pro správu nebo podobné uživatele v počítači.</span><span class="sxs-lookup"><span data-stu-id="2c41e-112">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="2c41e-113">Pro [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikace, to znamená, že bude uživatel potřebovat oprávnění správce k instalaci aplikace, bez ohledu na úroveň zabezpečení, který je určený aplikací.</span><span class="sxs-lookup"><span data-stu-id="2c41e-113">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="2c41e-114">Po instalaci aplikace, může uživatel spustit aplikaci bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="2c41e-114">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="2c41e-115">Během instalace, uživatelům se zobrazí výzva k instalaci <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti, pokud není přítomen v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="2c41e-115">During installation, users will be prompted to install the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component if it is not present on the destination computer.</span></span>  
  
 <span data-ttu-id="2c41e-116">Jako alternativu k zavedení spouštěcího programu, můžete předem nasadit <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti pomocí systému distribuce elektronického software jako Microsoft Systems Management Server.</span><span class="sxs-lookup"><span data-stu-id="2c41e-116">As an alternative to bootstrapping, you can pre-deploy the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component by using an electronic software distribution system like Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c41e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c41e-117">See also</span></span>  
 [<span data-ttu-id="2c41e-118">Postupy: Instalace předpokladů s aplikací ClickOnce</span><span class="sxs-lookup"><span data-stu-id="2c41e-118">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="2c41e-119">Komponenta PrintForm</span><span class="sxs-lookup"><span data-stu-id="2c41e-119">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
