---
title: Bezpečnostní oprávnění k přesměrování vazby sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: b59689e78f901637674c0a1df28ed74411e8e7c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921377"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="55664-102">Bezpečnostní oprávnění k přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="55664-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="55664-103">Explicitní přesměrování vazeb sestavení v konfiguračním souboru aplikace vyžaduje oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="55664-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="55664-104">To platí pro přesměrování sestavení rozhraní .NET Framework a sestavení třetích stran.</span><span class="sxs-lookup"><span data-stu-id="55664-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="55664-105">Oprávnění je uděleno nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku <xref:System.Security.Permissions.SecurityPermission>na.</span><span class="sxs-lookup"><span data-stu-id="55664-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="55664-106">Spravovaná sestavení nemají ve výchozím nastavení žádná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="55664-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="55664-107">Oprávnění zabezpečení je uděleno aplikacím spuštěným v důvěryhodné zóně (místním počítači) a zóně intranetu.</span><span class="sxs-lookup"><span data-stu-id="55664-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="55664-108">Aplikace spuštěné v zóně Internet jsou striktně zakázané při provádění přesměrování vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="55664-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="55664-109">Oprávnění není vyžadováno, pokud je přesměrování sestavení provedeno v souboru zásad vydavatele, který je řízen vydavatelem komponenty, nebo v konfiguračním souboru, který je řízen správcem.</span><span class="sxs-lookup"><span data-stu-id="55664-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="55664-110">Nicméně oprávnění je vyžadováno, aby aplikace explicitně ignorovala zásady vydavatele pomocí [ \<elementu publisherPolicy Apply = "No"/>](./file-schema/runtime/publisherpolicy-element.md) v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="55664-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="55664-111">Následující tabulka ukazuje výchozí nastavení zabezpečení pro příznak **BindingRedirects** .</span><span class="sxs-lookup"><span data-stu-id="55664-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="55664-112">Zóny</span><span class="sxs-lookup"><span data-stu-id="55664-112">Zone</span></span>|<span data-ttu-id="55664-113">Nastavení příznaku BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="55664-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="55664-114">Důvěryhodná zóna (místní počítač)</span><span class="sxs-lookup"><span data-stu-id="55664-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="55664-115">**PNETE**</span><span class="sxs-lookup"><span data-stu-id="55664-115">**ON**</span></span>|  
|<span data-ttu-id="55664-116">Intranet Zone</span><span class="sxs-lookup"><span data-stu-id="55664-116">Intranet Zone</span></span>|<span data-ttu-id="55664-117">**PNETE**</span><span class="sxs-lookup"><span data-stu-id="55664-117">**ON**</span></span>|  
|<span data-ttu-id="55664-118">Zóna Internetu</span><span class="sxs-lookup"><span data-stu-id="55664-118">Internet Zone</span></span>|<span data-ttu-id="55664-119">**ZAOKROUHL**</span><span class="sxs-lookup"><span data-stu-id="55664-119">**OFF**</span></span>|  
|<span data-ttu-id="55664-120">Nedůvěryhodné zóny</span><span class="sxs-lookup"><span data-stu-id="55664-120">Untrusted zones</span></span>|<span data-ttu-id="55664-121">**ZAOKROUHL**</span><span class="sxs-lookup"><span data-stu-id="55664-121">**OFF**</span></span>|  
  
 <span data-ttu-id="55664-122">Správce může změnit tato nastavení zabezpečení na podporu nebo omezení konkrétních scénářů v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="55664-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="55664-123">Neexistují žádné nástroje pro změnu nastavení příznaku **BindingRedirects** z výchozí hodnoty. Správce musí ručně upravit soubor Security. config v počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="55664-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55664-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55664-124">See also</span></span>

- <span data-ttu-id="55664-125">[Soubory zásad vydavatele a souběžné spouštění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55664-125">[Publisher Policy Files and Side-by-Side Execution](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="55664-126">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="55664-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="55664-127">Souběžné spouštění</span><span class="sxs-lookup"><span data-stu-id="55664-127">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
