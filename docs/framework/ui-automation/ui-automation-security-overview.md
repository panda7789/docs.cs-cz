---
title: "Přehled zabezpečení automatizace uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: ee3847164ecdc9b9868d806b5a1394ffca0bbd31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="e59de-102">Přehled zabezpečení automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e59de-102">UI Automation Security Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="e59de-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e59de-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e59de-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e59de-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e59de-105">Tento přehled popisuje model zabezpečení pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] v [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e59de-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span></span>  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a><span data-ttu-id="e59de-106">řízení uživatelských účtů</span><span class="sxs-lookup"><span data-stu-id="e59de-106">User Account Control</span></span>  
 <span data-ttu-id="e59de-107">Zabezpečení je hlavní fokus [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] a mezi inovace přístup je schopnost uživatelům spustit jako standardní uživatelé (bez oprávnění správce) bez nutně se blokovat spouštění aplikací a služeb, které vyžadují vyšší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e59de-107">Security is a major focus of [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>  
  
 <span data-ttu-id="e59de-108">V [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], většina aplikací se dodává s standard nebo token pro správu.</span><span class="sxs-lookup"><span data-stu-id="e59de-108">In [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="e59de-109">Pokud aplikace nemůže být identifikován jako aplikace pro správu, se spustí jako u standardní aplikace ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e59de-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="e59de-110">Předtím, než aplikace identifikovat jako správce může být spuštěn, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] zobrazí výzvu k souhlasu, a spusťte aplikaci jako zvýšených oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e59de-110">Before an application identified as administrative can be launched, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="e59de-111">Řádku souhlasu se zobrazí ve výchozím nastavení, i pokud je uživatel členem místní skupiny Administrators, protože správce spustit jako standardní uživatelé, dokud aplikace nebo součást systému, který vyžaduje pověření správce požádá o oprávnění ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="e59de-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="e59de-112">Úlohy, které vyžadují vyšší oprávnění</span><span class="sxs-lookup"><span data-stu-id="e59de-112">Tasks Requiring Higher Privileges</span></span>  
 <span data-ttu-id="e59de-113">Když se uživatel pokusí provést úlohu, která vyžaduje oprávnění správce, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] uvede dialogové okno s dotazem uživatele o souhlas s pokračovat.</span><span class="sxs-lookup"><span data-stu-id="e59de-113">When a user attempts to perform a task that requires administrative privileges, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="e59de-114">Toto dialogové okno je chráněný před komunikaci mezi procesy, tak, aby škodlivého softwaru nejde simulovat vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="e59de-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="e59de-115">Podobně nelze na obrazovce přihlášení k ploše přistupovat normálně jinými procesy.</span><span class="sxs-lookup"><span data-stu-id="e59de-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>  
  
 <span data-ttu-id="e59de-116">Klienti automatizace uživatelského rozhraní musí komunikovat s jinými procesy, některé z nich pravděpodobně spuštěná na vyšší úrovni oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e59de-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="e59de-117">Klienti také může potřebovat přístup k systému dialogových oken, které nejsou standardně viditelné pro jiné procesy.</span><span class="sxs-lookup"><span data-stu-id="e59de-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="e59de-118">Proto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klientů musí být důvěryhodný systému a musí být spuštěna s zvláštní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e59de-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>  
  
 <span data-ttu-id="e59de-119">Aby byl důvěryhodný ke komunikaci s aplikací, které běží na vyšší úrovni oprávnění, musí být podepsané aplikace.</span><span class="sxs-lookup"><span data-stu-id="e59de-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a><span data-ttu-id="e59de-120">Soubory manifestu</span><span class="sxs-lookup"><span data-stu-id="e59de-120">Manifest Files</span></span>  
 <span data-ttu-id="e59de-121">K získání přístupu k systému chráněného [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], aplikace musí být vytvořené s nástroji soubor manifestu, který obsahuje speciální atribut v souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="e59de-121">To gain access to the protected system [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], applications must be built with a manifest file that includes a special attribute in the manifest file.</span></span> <span data-ttu-id="e59de-122">To `uiAccess` atribut je součástí `requestedExecutionLevel` značka, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e59de-122">This `uiAccess` attribute is included in the `requestedExecutionLevel` tag, as follows:</span></span>  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 <span data-ttu-id="e59de-123">Hodnota `level` atribut v tento kód je pouze příklad.</span><span class="sxs-lookup"><span data-stu-id="e59de-123">The value of the `level` attribute in this code is an example only.</span></span>  
  
 <span data-ttu-id="e59de-124">`UIAccess`je "false" ve výchozím nastavení; To znamená, pokud je vynechán atribut, nebo pokud neexistuje žádný manifest pro sestavení, aplikace nebude schopen získat přístup k chráněné [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e59de-124">`UIAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="e59de-125">Další informace o [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] zabezpečení, podepisování aplikací a na vytváření sestavení manifesty, najdete v části "Vývojáře osvědčené postupy a pokyny pro aplikace v prostředí nejnižšího" na [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).</span><span class="sxs-lookup"><span data-stu-id="e59de-125">For more information on [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] security, on signing applications, and on creating assembly manifests, see "Developer Best Practices and Guidelines for Applications in a Least Privileged Environment" on  [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).</span></span>
