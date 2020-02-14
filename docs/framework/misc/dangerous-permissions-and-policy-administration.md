---
title: Správa nebezpečných oprávnění a zásad
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: 026697feec7afe950628639c5e595ba0a0220b97
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217145"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="70caf-102">Správa nebezpečných oprávnění a zásad</span><span class="sxs-lookup"><span data-stu-id="70caf-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="70caf-103">Některé z chráněných operací, pro které .NET Framework poskytují oprávnění, můžou potenciálně dovolit obejít systém zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="70caf-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="70caf-104">Tato nebezpečná oprávnění by měla být udělena pouze důvěryhodnému kódu a pak pouze podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="70caf-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="70caf-105">Není obvykle žádná obrana proti škodlivému kódu, pokud jim byla udělena tato oprávnění.</span><span class="sxs-lookup"><span data-stu-id="70caf-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70caf-106">V .NET Framework 4 existovaly důležité změny modelu a terminologie zabezpečení .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70caf-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="70caf-107">Další informace o těchto změnách najdete v tématu [změny zabezpečení](../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="70caf-107">For more information about these changes, see [Security Changes](../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="70caf-108">Nebezpečná oprávnění jsou vysvětlena v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="70caf-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="70caf-109">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="70caf-109">Permission</span></span>|<span data-ttu-id="70caf-110">Potenciální riziko</span><span class="sxs-lookup"><span data-stu-id="70caf-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="70caf-111">Umožňuje spravovanému kódu volat do nespravovaného kódu, který je často nebezpečný.</span><span class="sxs-lookup"><span data-stu-id="70caf-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="70caf-112">Bez ověření může kód provádět cokoli.</span><span class="sxs-lookup"><span data-stu-id="70caf-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="70caf-113">Neověřené legitimace můžou podvést zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="70caf-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="70caf-114">Možnost upravovat zásady zabezpečení může zabezpečení zakázat.</span><span class="sxs-lookup"><span data-stu-id="70caf-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="70caf-115">Použití serializace může obejít mechanismy přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="70caf-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="70caf-116">Podrobnosti najdete v tématu [zabezpečení a serializace](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="70caf-116">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="70caf-117">Možnost nastavit aktuální objekt zabezpečení může být obtížné zabezpečení na základě rolí.</span><span class="sxs-lookup"><span data-stu-id="70caf-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="70caf-118">Manipulace s vlákny je nebezpečná, protože stav zabezpečení je přidružený k vláknům.</span><span class="sxs-lookup"><span data-stu-id="70caf-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="70caf-119">Může použít soukromé členy k přepřipravenosti mechanismů přístupu.</span><span class="sxs-lookup"><span data-stu-id="70caf-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70caf-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="70caf-120">See also</span></span>

- [<span data-ttu-id="70caf-121">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="70caf-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
