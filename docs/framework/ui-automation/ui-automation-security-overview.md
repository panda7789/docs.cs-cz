---
title: Přehled zabezpečení automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 70d24c3dcc531abcec6d4dce75b5f0b31757e0c0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448780"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="d2fd4-102">Přehled zabezpečení automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2fd4-102">UI Automation Security Overview</span></span>

> [!NOTE]
> <span data-ttu-id="d2fd4-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d2fd4-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="d2fd4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="d2fd4-105">Tento přehled popisuje model zabezpečení pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in Windows Vista.</span></span>

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a><span data-ttu-id="d2fd4-106">řízení uživatelských účtů</span><span class="sxs-lookup"><span data-stu-id="d2fd4-106">User Account Control</span></span>

<span data-ttu-id="d2fd4-107">Zabezpečení je hlavním cílem systému Windows Vista a mezi inovacemi je možnost spouštění uživatelů jako standardní (bez oprávnění správce), aniž by bylo nutné zablokovat spouštění aplikací a služeb, které vyžadují vyšší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-107">Security is a major focus of Windows Vista and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>

<span data-ttu-id="d2fd4-108">V systému Windows Vista je většina aplikací dodávána buď s tokenem Standard, nebo s tokenem správce.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-108">In Windows Vista, most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="d2fd4-109">Pokud aplikaci nelze identifikovat jako aplikaci pro správu, je ve výchozím nastavení spuštěna jako standardní aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="d2fd4-110">Předtím, než bude možné spustit aplikaci určenou jako správce, systém Windows Vista vyzve uživatele k zadání souhlasu pro spuštění aplikace jako vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-110">Before an application identified as administrative can be launched, Windows Vista prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="d2fd4-111">Ve výchozím nastavení se zobrazí výzva k vyjádření souhlasu, a to i v případě, že je uživatel členem místní skupiny Administrators, protože správci spouštějí jako standardní uživatelé, dokud nebude aplikace nebo systémová komponenta vyžadující oprávnění ke spuštění vyžadovat oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="d2fd4-112">Úlohy vyžadující vyšší oprávnění</span><span class="sxs-lookup"><span data-stu-id="d2fd4-112">Tasks Requiring Higher Privileges</span></span>

<span data-ttu-id="d2fd4-113">Když se uživatel pokusí provést úlohu, která vyžaduje oprávnění správce, systém Windows Vista zobrazí dialogové okno s výzvou, aby bylo možné pokračovat v souhlasu uživatele.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-113">When a user attempts to perform a task that requires administrative privileges, Windows Vista presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="d2fd4-114">Toto dialogové okno je chráněno proti komunikaci mezi procesy, takže škodlivý software nemůže simulovat uživatelský vstup.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="d2fd4-115">Podobně může být obrazovka pro přihlášení k ploše běžně dostupná pro jiné procesy.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>

<span data-ttu-id="d2fd4-116">Klienti automatizace uživatelského rozhraní musí komunikovat s jinými procesy, některé z nich možná běží na vyšší úrovni oprávnění.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="d2fd4-117">Klienti taky můžou potřebovat přístup k systémovým dialogovým oknům, která nejsou normálně viditelná pro jiné procesy.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="d2fd4-118">Proto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienti musí být systémem důvěryhodné a musí běžet se speciálními oprávněními.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>

<span data-ttu-id="d2fd4-119">Aby bylo možné komunikovat s aplikacemi spuštěnými na vyšší úrovni oprávnění, musí být aplikace podepsány.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a><span data-ttu-id="d2fd4-120">Soubory manifestu</span><span class="sxs-lookup"><span data-stu-id="d2fd4-120">Manifest Files</span></span>

<span data-ttu-id="d2fd4-121">Chcete-li získat přístup k uživatelskému rozhraní chráněného systému, musí být aplikace sestaveny pomocí souboru manifestu, který obsahuje atribut `uiAccess` ve značce `requestedExecutionLevel` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d2fd4-121">To gain access to the protected system UI, applications must be built with a manifest file that includes the `uiAccess` attribute in the `requestedExecutionLevel` tag, as follows:</span></span>

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

<span data-ttu-id="d2fd4-122">Hodnota atributu `level` v tomto kódu je pouze příklad.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-122">The value of the `level` attribute in this code is an example only.</span></span>

<span data-ttu-id="d2fd4-123">ve výchozím nastavení má `uiAccess` hodnotu false; To znamená, že pokud je atribut vynechán, nebo pokud neexistuje manifest pro sestavení, aplikace nebude moci získat přístup k chráněnému uživatelskému rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d2fd4-123">`uiAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected UI.</span></span>
