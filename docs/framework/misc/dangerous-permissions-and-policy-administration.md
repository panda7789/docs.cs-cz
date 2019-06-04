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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 17a596d9fc223dc53268ae9c91f7d02357b0a9b8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489973"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="b7eb5-102">Správa nebezpečných oprávnění a zásad</span><span class="sxs-lookup"><span data-stu-id="b7eb5-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="b7eb5-103">Některé z chráněné operace, pro které rozhraní .NET Framework poskytuje oprávnění potenciálně může mít systém zabezpečení obcházení.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="b7eb5-104">Tato nebezpečných oprávnění by se měly provádět jenom pro důvěryhodného kódu a pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="b7eb5-105">Je obvykle žádnou obranu proti škodlivým kódem Pokud jsou udělena tato oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7eb5-106">V rozhraní .NET Framework 4 byly důležité změny modelu zabezpečení rozhraní .NET Framework a terminologii.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="b7eb5-107">Další informace o těchto změnách najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="b7eb5-107">For more information about these changes, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="b7eb5-108">Nebezpečná oprávnění jsou vysvětlené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="b7eb5-109">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="b7eb5-109">Permission</span></span>|<span data-ttu-id="b7eb5-110">Potenciální riziko</span><span class="sxs-lookup"><span data-stu-id="b7eb5-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="b7eb5-111">Umožňuje spravovanému kódu volat nespravovaný kód, který je často nebezpečné.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="b7eb5-112">Bez ověřování kód dělat cokoli.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="b7eb5-113">Neplatná legitimace může oklamat zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="b7eb5-114">Možnost upravit zásady zabezpečení můžete zakázat zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="b7eb5-115">Použití serializace může obejít mechanismy usnadnění.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="b7eb5-116">Podrobnosti najdete v tématu [zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="b7eb5-116">For details, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="b7eb5-117">Možnost nastavit aktuální objekt zabezpečení můžou přimět zabezpečení na základě rolí.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="b7eb5-118">Manipulace s vlákny je nebezpečné z důvodu stavu zabezpečení související s vlákny.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="b7eb5-119">Můžete použít soukromé členy k překonání mechanismů usnadnění.</span><span class="sxs-lookup"><span data-stu-id="b7eb5-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7eb5-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7eb5-120">See also</span></span>

- [<span data-ttu-id="b7eb5-121">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="b7eb5-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
