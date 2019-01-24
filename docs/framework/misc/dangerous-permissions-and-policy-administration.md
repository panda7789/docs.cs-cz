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
ms.openlocfilehash: 281582b04aabd8a18af8bf17091979385d009ee8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536539"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="53c51-102">Správa nebezpečných oprávnění a zásad</span><span class="sxs-lookup"><span data-stu-id="53c51-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="53c51-103">Některé z chráněné operace, pro které rozhraní .NET Framework poskytuje oprávnění potenciálně může mít systém zabezpečení obcházení.</span><span class="sxs-lookup"><span data-stu-id="53c51-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="53c51-104">Tato nebezpečných oprávnění by se měly provádět jenom pro důvěryhodného kódu a pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="53c51-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="53c51-105">Je obvykle žádnou obranu proti škodlivým kódem Pokud jsou udělena tato oprávnění.</span><span class="sxs-lookup"><span data-stu-id="53c51-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53c51-106">V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], byly důležité změny v modelu zabezpečení rozhraní .NET Framework a terminologii.</span><span class="sxs-lookup"><span data-stu-id="53c51-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="53c51-107">Další informace o těchto změnách najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="53c51-107">For more information about these changes, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="53c51-108">Nebezpečná oprávnění jsou vysvětlené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="53c51-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="53c51-109">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="53c51-109">Permission</span></span>|<span data-ttu-id="53c51-110">Potenciální riziko</span><span class="sxs-lookup"><span data-stu-id="53c51-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="53c51-111">Umožňuje spravovanému kódu volat nespravovaný kód, který je často nebezpečné.</span><span class="sxs-lookup"><span data-stu-id="53c51-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="53c51-112">Bez ověřování kód dělat cokoli.</span><span class="sxs-lookup"><span data-stu-id="53c51-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="53c51-113">Neplatná legitimace může oklamat zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="53c51-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="53c51-114">Možnost upravit zásady zabezpečení můžete zakázat zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="53c51-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="53c51-115">Použití serializace může obejít mechanismy usnadnění.</span><span class="sxs-lookup"><span data-stu-id="53c51-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="53c51-116">Podrobnosti najdete v tématu [zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="53c51-116">For details, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="53c51-117">Možnost nastavit aktuální objekt zabezpečení můžou přimět zabezpečení na základě rolí.</span><span class="sxs-lookup"><span data-stu-id="53c51-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="53c51-118">Manipulace s vlákny je nebezpečné z důvodu stavu zabezpečení související s vlákny.</span><span class="sxs-lookup"><span data-stu-id="53c51-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="53c51-119">Můžete použít soukromé členy k překonání mechanismů usnadnění.</span><span class="sxs-lookup"><span data-stu-id="53c51-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53c51-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53c51-120">See also</span></span>
- [<span data-ttu-id="53c51-121">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="53c51-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
