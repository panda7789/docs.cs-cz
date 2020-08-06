---
title: Správa nebezpečných oprávnění a zásad
description: Viz odkazy na různá nebezpečná oprávnění v .NET. Tato oprávnění by se měla udělit jenom důvěryhodnému kódu a jenom v případě potřeby.
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: 1d3fb53775a4d88f9372b582189a38e18376761a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855813"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="06964-104">Správa nebezpečných oprávnění a zásad</span><span class="sxs-lookup"><span data-stu-id="06964-104">Dangerous Permissions and Policy Administration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="06964-105">Některé z chráněných operací, pro které .NET Framework poskytují oprávnění, můžou potenciálně dovolit obejít systém zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="06964-105">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="06964-106">Tato nebezpečná oprávnění by měla být udělena pouze důvěryhodnému kódu a pak pouze podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="06964-106">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="06964-107">Není obvykle žádná obrana proti škodlivému kódu, pokud jim byla udělena tato oprávnění.</span><span class="sxs-lookup"><span data-stu-id="06964-107">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06964-108">V .NET Framework 4 existovaly důležité změny modelu a terminologie zabezpečení .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06964-108">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="06964-109">Další informace o těchto změnách najdete v tématu [změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="06964-109">For more information about these changes, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="06964-110">Nebezpečná oprávnění jsou vysvětlena v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="06964-110">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="06964-111">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="06964-111">Permission</span></span>|<span data-ttu-id="06964-112">Potenciální riziko</span><span class="sxs-lookup"><span data-stu-id="06964-112">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="06964-113">Umožňuje spravovanému kódu volat do nespravovaného kódu, který je často nebezpečný.</span><span class="sxs-lookup"><span data-stu-id="06964-113">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="06964-114">Bez ověření může kód provádět cokoli.</span><span class="sxs-lookup"><span data-stu-id="06964-114">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="06964-115">Neověřené legitimace můžou podvést zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="06964-115">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="06964-116">Možnost upravovat zásady zabezpečení může zabezpečení zakázat.</span><span class="sxs-lookup"><span data-stu-id="06964-116">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="06964-117">Použití serializace může obejít mechanismy přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="06964-117">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="06964-118">Podrobnosti najdete v tématu [zabezpečení a serializace](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="06964-118">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="06964-119">Možnost nastavit aktuální objekt zabezpečení může být obtížné zabezpečení na základě rolí.</span><span class="sxs-lookup"><span data-stu-id="06964-119">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="06964-120">Manipulace s vlákny je nebezpečná, protože stav zabezpečení je přidružený k vláknům.</span><span class="sxs-lookup"><span data-stu-id="06964-120">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="06964-121">Může použít soukromé členy k přepřipravenosti mechanismů přístupu.</span><span class="sxs-lookup"><span data-stu-id="06964-121">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06964-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="06964-122">See also</span></span>

- [<span data-ttu-id="06964-123">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="06964-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
