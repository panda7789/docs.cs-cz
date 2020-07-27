---
title: Přehled zabezpečení automatizace uživatelského rozhraní
description: Přečtěte si přehled modelu zabezpečení pro automatizaci uživatelského rozhraní Microsoft. Pochopení řízení uživatelských účtů, úloh, které vyžadují vyšší oprávnění, a souborů manifestu.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: d483f282db8ce8e5653d6d83361fa44df05f63f5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163142"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="c1a4c-104">Přehled zabezpečení automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1a4c-104">UI Automation Security Overview</span></span>

> [!NOTE]
> <span data-ttu-id="c1a4c-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c1a4c-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="c1a4c-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="c1a4c-107">Tento přehled popisuje model zabezpečení nástroje [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-107">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in Windows Vista.</span></span>

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a><span data-ttu-id="c1a4c-108">řízení uživatelských účtů</span><span class="sxs-lookup"><span data-stu-id="c1a4c-108">User Account Control</span></span>

<span data-ttu-id="c1a4c-109">Zabezpečení je hlavním cílem systému Windows Vista a mezi inovacemi je možnost spouštění uživatelů jako standardní (bez oprávnění správce), aniž by bylo nutné zablokovat spouštění aplikací a služeb, které vyžadují vyšší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-109">Security is a major focus of Windows Vista and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>

<span data-ttu-id="c1a4c-110">V systému Windows Vista je většina aplikací dodávána buď s tokenem Standard, nebo s tokenem správce.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-110">In Windows Vista, most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="c1a4c-111">Pokud aplikaci nelze identifikovat jako aplikaci pro správu, je ve výchozím nastavení spuštěna jako standardní aplikace.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-111">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="c1a4c-112">Předtím, než bude možné spustit aplikaci určenou jako správce, systém Windows Vista vyzve uživatele k zadání souhlasu pro spuštění aplikace jako vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-112">Before an application identified as administrative can be launched, Windows Vista prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="c1a4c-113">Ve výchozím nastavení se zobrazí výzva k vyjádření souhlasu, a to i v případě, že je uživatel členem místní skupiny Administrators, protože správci spouštějí jako standardní uživatelé, dokud nebude aplikace nebo systémová komponenta vyžadující oprávnění ke spuštění vyžadovat oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-113">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="c1a4c-114">Úlohy vyžadující vyšší oprávnění</span><span class="sxs-lookup"><span data-stu-id="c1a4c-114">Tasks Requiring Higher Privileges</span></span>

<span data-ttu-id="c1a4c-115">Když se uživatel pokusí provést úlohu, která vyžaduje oprávnění správce, systém Windows Vista zobrazí dialogové okno s výzvou, aby bylo možné pokračovat v souhlasu uživatele.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-115">When a user attempts to perform a task that requires administrative privileges, Windows Vista presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="c1a4c-116">Toto dialogové okno je chráněno proti komunikaci mezi procesy, takže škodlivý software nemůže simulovat uživatelský vstup.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-116">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="c1a4c-117">Podobně může být obrazovka pro přihlášení k ploše běžně dostupná pro jiné procesy.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-117">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>

<span data-ttu-id="c1a4c-118">Klienti automatizace uživatelského rozhraní musí komunikovat s jinými procesy, některé z nich možná běží na vyšší úrovni oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-118">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="c1a4c-119">Klienti taky můžou potřebovat přístup k systémovým dialogovým oknům, která nejsou normálně viditelná pro jiné procesy.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-119">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="c1a4c-120">Proto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] musí být klienti důvěryhodný systémem a musí běžet se speciálními oprávněními.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-120">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>

<span data-ttu-id="c1a4c-121">Aby bylo možné komunikovat s aplikacemi spuštěnými na vyšší úrovni oprávnění, musí být aplikace podepsány.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-121">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a><span data-ttu-id="c1a4c-122">Soubory manifestu</span><span class="sxs-lookup"><span data-stu-id="c1a4c-122">Manifest Files</span></span>

<span data-ttu-id="c1a4c-123">Chcete-li získat přístup k uživatelskému rozhraní chráněného systému, aplikace musí být sestaveny pomocí souboru manifestu, který obsahuje `uiAccess` atribut ve `requestedExecutionLevel` značce, následovně:</span><span class="sxs-lookup"><span data-stu-id="c1a4c-123">To gain access to the protected system UI, applications must be built with a manifest file that includes the `uiAccess` attribute in the `requestedExecutionLevel` tag, as follows:</span></span>

```xml
<trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
  <security>
    <requestedPrivileges>
      <requestedExecutionLevel
        level="highestAvailable"
        uiAccess="true" />
    </requestedPrivileges>
  </security>
</trustInfo>
```

<span data-ttu-id="c1a4c-124">Hodnota `level` atributu v tomto kódu je pouze příklad.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-124">The value of the `level` attribute in this code is an example only.</span></span>

<span data-ttu-id="c1a4c-125">`uiAccess`má ve výchozím nastavení hodnotu false; To znamená, že pokud je atribut vynechán, nebo pokud neexistuje manifest pro sestavení, aplikace nebude moci získat přístup k chráněnému uživatelskému rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c1a4c-125">`uiAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected UI.</span></span>
