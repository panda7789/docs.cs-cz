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
ms.openlocfilehash: 15d28ff7d11b5d15ce44d9ab1f56548256850ff8
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645761"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="02516-102">Správa nebezpečných oprávnění a zásad</span><span class="sxs-lookup"><span data-stu-id="02516-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="02516-103">Několik chráněných operací, pro které rozhraní .NET Framework poskytuje oprávnění, může potenciálně umožnit obcházení systému zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="02516-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="02516-104">Tato nebezpečná oprávnění by měla být udělena pouze důvěryhodnému kódu a pak pouze podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="02516-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="02516-105">Obvykle neexistuje žádná obrana proti škodlivému kódu, pokud je udělena tato oprávnění.</span><span class="sxs-lookup"><span data-stu-id="02516-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02516-106">V rozhraní .NET Framework 4 došlo k důležitým změnám modelu zabezpečení a terminologie rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="02516-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="02516-107">Další informace o těchto změnách naleznete v [tématu Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="02516-107">For more information about these changes, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="02516-108">Nebezpečná oprávnění jsou vysvětlena v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="02516-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="02516-109">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="02516-109">Permission</span></span>|<span data-ttu-id="02516-110">Potenciální riziko</span><span class="sxs-lookup"><span data-stu-id="02516-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="02516-111">Umožňuje spravovanému kódu volat do nespravovaného kódu, což je často nebezpečné.</span><span class="sxs-lookup"><span data-stu-id="02516-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="02516-112">Bez ověření může kód dělat cokoliv.</span><span class="sxs-lookup"><span data-stu-id="02516-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="02516-113">Zneplatněné důkazy mohou oklamat bezpečnostní politiku.</span><span class="sxs-lookup"><span data-stu-id="02516-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="02516-114">Možnost změny zásad zabezpečení může zakázat zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="02516-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="02516-115">Použití serializace může obejít mechanismy usnadnění.</span><span class="sxs-lookup"><span data-stu-id="02516-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="02516-116">Podrobnosti naleznete v [tématu Zabezpečení a serializace](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="02516-116">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="02516-117">Možnost nastavit aktuální jistinu může oklamat zabezpečení založené na rolích.</span><span class="sxs-lookup"><span data-stu-id="02516-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="02516-118">Manipulace s vlákny je nebezpečná z důvodu stavu zabezpečení spojeného s vlákny.</span><span class="sxs-lookup"><span data-stu-id="02516-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="02516-119">Můžete použít soukromé členy porazit mechanismy usnadnění.</span><span class="sxs-lookup"><span data-stu-id="02516-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02516-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="02516-120">See also</span></span>

- [<span data-ttu-id="02516-121">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="02516-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
