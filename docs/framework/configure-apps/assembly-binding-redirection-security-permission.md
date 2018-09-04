---
title: Bezpečnostní oprávnění k přesměrování vazby sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b9b9ac5c4e8ce08b9f926b0cdf7149dbdd9ac2da
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501430"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="1c02c-102">Bezpečnostní oprávnění k přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="1c02c-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="1c02c-103">Explicitní přesměrování vazeb sestavení v konfiguračním souboru aplikace vyžaduje oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1c02c-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="1c02c-104">To platí pro přesměrování sestavení rozhraní .NET Framework a sestavení třetích stran.</span><span class="sxs-lookup"><span data-stu-id="1c02c-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="1c02c-105">Oprávnění je udělován nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="1c02c-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="1c02c-106">Spravovaná sestavení nemají žádná oprávnění ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="1c02c-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="1c02c-107">Aplikace běžící v zóně důvěryhodných (místní počítač) a zóny intranetu je uděleno oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1c02c-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="1c02c-108">Aplikace běžící v zóně Internet výhradně zakázáno provádět přesměrování vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="1c02c-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="1c02c-109">Oprávnění není povinný, pokud přesměrování sestavení se provádí v souboru zásad vydavatele, které řídí součásti vydavatele nebo v konfiguračním souboru počítače, které řídí správce.</span><span class="sxs-lookup"><span data-stu-id="1c02c-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="1c02c-110">Však oprávnění není vyžadován pro aplikaci explicitně ignorovat pomocí zásady vydavatele [ \<publisherPolicy použít = "žádný" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) prvku v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c02c-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="1c02c-111">V následující tabulce jsou uvedeny výchozí nastavení zabezpečení **BindingRedirects** příznak.</span><span class="sxs-lookup"><span data-stu-id="1c02c-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="1c02c-112">Zóna</span><span class="sxs-lookup"><span data-stu-id="1c02c-112">Zone</span></span>|<span data-ttu-id="1c02c-113">Nastavení příznaku BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="1c02c-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="1c02c-114">Zóny důvěryhodných serverů (místní počítač)</span><span class="sxs-lookup"><span data-stu-id="1c02c-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="1c02c-115">**DÁLE**</span><span class="sxs-lookup"><span data-stu-id="1c02c-115">**ON**</span></span>|  
|<span data-ttu-id="1c02c-116">Zóny intranetu</span><span class="sxs-lookup"><span data-stu-id="1c02c-116">Intranet Zone</span></span>|<span data-ttu-id="1c02c-117">**DÁLE**</span><span class="sxs-lookup"><span data-stu-id="1c02c-117">**ON**</span></span>|  
|<span data-ttu-id="1c02c-118">Zóna Internetu</span><span class="sxs-lookup"><span data-stu-id="1c02c-118">Internet Zone</span></span>|<span data-ttu-id="1c02c-119">**VYPNOUT**</span><span class="sxs-lookup"><span data-stu-id="1c02c-119">**OFF**</span></span>|  
|<span data-ttu-id="1c02c-120">Nedůvěryhodné zóny</span><span class="sxs-lookup"><span data-stu-id="1c02c-120">Untrusted zones</span></span>|<span data-ttu-id="1c02c-121">**VYPNOUT**</span><span class="sxs-lookup"><span data-stu-id="1c02c-121">**OFF**</span></span>|  
  
 <span data-ttu-id="1c02c-122">Správce může změnit nastavení zabezpečení pro podporu nebo omezit určité scénáře na daný počítač.</span><span class="sxs-lookup"><span data-stu-id="1c02c-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="1c02c-123">Nejsou žádné nástroje pro změnu **BindingRedirects** příznak nastavení z výchozí hodnoty; správce musíte ručně upravit soubor Security.config na počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="1c02c-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c02c-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c02c-124">See Also</span></span>  
 [<span data-ttu-id="1c02c-125">Soubory zásad vydavatele a spuštění vedle sebe</span><span class="sxs-lookup"><span data-stu-id="1c02c-125">Publisher Policy Files and Side-by-Side Execution</span></span>](https://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="1c02c-126">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="1c02c-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="1c02c-127">Souběžné spouštění</span><span class="sxs-lookup"><span data-stu-id="1c02c-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
