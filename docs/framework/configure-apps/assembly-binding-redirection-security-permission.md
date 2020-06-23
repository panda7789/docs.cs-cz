---
title: Bezpečnostní oprávnění k přesměrování vazby sestavení
description: Přečtěte si o oprávnění zabezpečení vyžadovaného pro explicitní přesměrování vazby sestavení v konfiguračním souboru aplikace v rozhraní .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: a8596bcac4efb0aea07efcfde6726d8bbf148c24
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105088"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="c55f5-103">Bezpečnostní oprávnění k přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="c55f5-103">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="c55f5-104">Explicitní přesměrování vazeb sestavení v konfiguračním souboru aplikace vyžaduje oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c55f5-104">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="c55f5-105">To platí pro přesměrování sestavení rozhraní .NET Framework a sestavení třetích stran.</span><span class="sxs-lookup"><span data-stu-id="c55f5-105">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="c55f5-106">Oprávnění je uděleno nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku na <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="c55f5-106">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="c55f5-107">Spravovaná sestavení nemají ve výchozím nastavení žádná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c55f5-107">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="c55f5-108">Oprávnění zabezpečení je uděleno aplikacím spuštěným v důvěryhodné zóně (místním počítači) a zóně intranetu.</span><span class="sxs-lookup"><span data-stu-id="c55f5-108">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="c55f5-109">Aplikace spuštěné v zóně Internet jsou striktně zakázané při provádění přesměrování vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="c55f5-109">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="c55f5-110">Oprávnění není vyžadováno, pokud je přesměrování sestavení provedeno v souboru zásad vydavatele, který je řízen vydavatelem komponenty, nebo v konfiguračním souboru, který je řízen správcem.</span><span class="sxs-lookup"><span data-stu-id="c55f5-110">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="c55f5-111">Nicméně oprávnění je vyžadováno, aby aplikace explicitně ignorovala zásady vydavatele pomocí [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) elementu v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="c55f5-111">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="c55f5-112">Následující tabulka ukazuje výchozí nastavení zabezpečení pro příznak **BindingRedirects** .</span><span class="sxs-lookup"><span data-stu-id="c55f5-112">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="c55f5-113">Zóna</span><span class="sxs-lookup"><span data-stu-id="c55f5-113">Zone</span></span>|<span data-ttu-id="c55f5-114">Nastavení příznaku BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="c55f5-114">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="c55f5-115">Důvěryhodná zóna (místní počítač)</span><span class="sxs-lookup"><span data-stu-id="c55f5-115">Trusted Zone (local machine)</span></span>|<span data-ttu-id="c55f5-116">**PNETE**</span><span class="sxs-lookup"><span data-stu-id="c55f5-116">**ON**</span></span>|  
|<span data-ttu-id="c55f5-117">Intranetová zóna</span><span class="sxs-lookup"><span data-stu-id="c55f5-117">Intranet Zone</span></span>|<span data-ttu-id="c55f5-118">**PNETE**</span><span class="sxs-lookup"><span data-stu-id="c55f5-118">**ON**</span></span>|  
|<span data-ttu-id="c55f5-119">Zóna Internetu</span><span class="sxs-lookup"><span data-stu-id="c55f5-119">Internet Zone</span></span>|<span data-ttu-id="c55f5-120">**ZAOKROUHL**</span><span class="sxs-lookup"><span data-stu-id="c55f5-120">**OFF**</span></span>|  
|<span data-ttu-id="c55f5-121">Nedůvěryhodné zóny</span><span class="sxs-lookup"><span data-stu-id="c55f5-121">Untrusted zones</span></span>|<span data-ttu-id="c55f5-122">**ZAOKROUHL**</span><span class="sxs-lookup"><span data-stu-id="c55f5-122">**OFF**</span></span>|  
  
 <span data-ttu-id="c55f5-123">Správce může změnit tato nastavení zabezpečení na podporu nebo omezení konkrétních scénářů v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="c55f5-123">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="c55f5-124">Neexistují žádné nástroje pro změnu nastavení příznaku **BindingRedirects** z výchozí hodnoty. Správce musí ručně upravit soubor Security.config v počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="c55f5-124">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55f5-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c55f5-125">See also</span></span>

- <span data-ttu-id="c55f5-126">[Soubory zásad vydavatele a souběžné spouštění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c55f5-126">[Publisher Policy Files and Side-by-Side Execution](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="c55f5-127">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="c55f5-127">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="c55f5-128">Souběžné spouštění</span><span class="sxs-lookup"><span data-stu-id="c55f5-128">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
