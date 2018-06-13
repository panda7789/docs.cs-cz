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
ms.openlocfilehash: ef9295028aeb7bfcc6df88e9c8bb7f80e2a31368
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743261"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="e4e31-102">Bezpečnostní oprávnění k přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="e4e31-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="e4e31-103">Explicitní přesměrování vazeb sestavení v konfiguračním souboru aplikace vyžaduje oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e4e31-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="e4e31-104">To platí pro přesměrování sestavení rozhraní .NET Framework a sestavení třetích stran.</span><span class="sxs-lookup"><span data-stu-id="e4e31-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="e4e31-105">Je povoleno nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznak na <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="e4e31-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="e4e31-106">Spravovaná sestavení mít žádná oprávnění ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e4e31-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="e4e31-107">Po udělení oprávnění zabezpečení k aplikacím spuštěným v zóně důvěryhodných (místní počítač) a zóny intranetu.</span><span class="sxs-lookup"><span data-stu-id="e4e31-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="e4e31-108">Aplikace běžící v zóně Internet výhradně nesmějí provádění sestavení – přesměrování vazby.</span><span class="sxs-lookup"><span data-stu-id="e4e31-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="e4e31-109">Pokud sestavení – přesměrování se provádí v souboru zásad vydavatele, které řídí součásti vydavatele nebo v konfiguračním souboru počítače, které řídí správce, není potřeba oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e4e31-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="e4e31-110">Je však oprávnění požadovaná pro aplikaci explicitně ignorovat pomocí zásad vydavatele [ \<publisherPolicy použít = "žádný" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="e4e31-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="e4e31-111">Následující tabulka uvádí výchozí nastavení zabezpečení **BindingRedirects** příznak.</span><span class="sxs-lookup"><span data-stu-id="e4e31-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="e4e31-112">zóny</span><span class="sxs-lookup"><span data-stu-id="e4e31-112">Zone</span></span>|<span data-ttu-id="e4e31-113">Nastavení příznaku BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="e4e31-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="e4e31-114">Zóny důvěryhodných serverů (místní počítač)</span><span class="sxs-lookup"><span data-stu-id="e4e31-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="e4e31-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="e4e31-115">**ON**</span></span>|  
|<span data-ttu-id="e4e31-116">Zónu intranetu</span><span class="sxs-lookup"><span data-stu-id="e4e31-116">Intranet Zone</span></span>|<span data-ttu-id="e4e31-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="e4e31-117">**ON**</span></span>|  
|<span data-ttu-id="e4e31-118">Zóna Internetu</span><span class="sxs-lookup"><span data-stu-id="e4e31-118">Internet Zone</span></span>|<span data-ttu-id="e4e31-119">**VYPNOUT**</span><span class="sxs-lookup"><span data-stu-id="e4e31-119">**OFF**</span></span>|  
|<span data-ttu-id="e4e31-120">Nedůvěryhodné zóny</span><span class="sxs-lookup"><span data-stu-id="e4e31-120">Untrusted zones</span></span>|<span data-ttu-id="e4e31-121">**VYPNOUT**</span><span class="sxs-lookup"><span data-stu-id="e4e31-121">**OFF**</span></span>|  
  
 <span data-ttu-id="e4e31-122">Správce můžete změnit tato nastavení zabezpečení pro podporu nebo omezit konkrétních scénářů v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="e4e31-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="e4e31-123">Neexistují žádné nástroje pro změnu **BindingRedirects** příznak nastavení z výchozího; správce musíte ručně upravit soubor Security.config na počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="e4e31-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e31-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4e31-124">See Also</span></span>  
 [<span data-ttu-id="e4e31-125">Vydavatel – soubory zásad a provádění vedle sebe</span><span class="sxs-lookup"><span data-stu-id="e4e31-125">Publisher Policy Files and Side-by-Side Execution</span></span>](http://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="e4e31-126">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="e4e31-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="e4e31-127">Souběžné spouštění</span><span class="sxs-lookup"><span data-stu-id="e4e31-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
