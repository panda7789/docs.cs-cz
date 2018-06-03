---
title: Zabezpečení v .NET
ms.date: 06/04/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, security
- security [.NET], about security
- application development [.NET], security
- security [.NET Framework]
- security [.NET]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e60f463d5a691cb84a30c169e471aa905b2db17
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728586"
---
# <a name="security-in-net"></a><span data-ttu-id="933d5-102">Zabezpečení v .NET</span><span class="sxs-lookup"><span data-stu-id="933d5-102">Security in .NET</span></span>
<span data-ttu-id="933d5-103">Modul common language runtime a .NET poskytují mnoho užitečných tříd a služby, které umožňuje vývojářům snadno psát kód, zabezpečení a umožňují správcům systému přizpůsobit oprávnění udělená kódu tak, aby měl přístup k chráněným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="933d5-103">The common language runtime and the .NET provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="933d5-104">Kromě toho modul runtime a .NET poskytují užitečné třídy a služby, které usnadňují použití kryptografie a na základě rolí zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="933d5-104">In addition, the runtime and the .NET provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="933d5-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="933d5-105">In This Section</span></span>  

 [<span data-ttu-id="933d5-106">Klíčové koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="933d5-106">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="933d5-107">Obsahuje přehled common language runtime funkce zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="933d5-107">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="933d5-108">Tato část je určen pro vývojáře a správce systému.</span><span class="sxs-lookup"><span data-stu-id="933d5-108">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="933d5-109">Zabezpečení na základě rolí</span><span class="sxs-lookup"><span data-stu-id="933d5-109">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="933d5-110">Popisuje, jak pracovat se zabezpečením na základě rolí v kódu.</span><span class="sxs-lookup"><span data-stu-id="933d5-110">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="933d5-111">Tato část je určen pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="933d5-111">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="933d5-112">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="933d5-112">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="933d5-113">Poskytuje přehled kryptografických služeb rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="933d5-113">Provides an overview of cryptographic services provided by .NET.</span></span> <span data-ttu-id="933d5-114">Tato část je určen pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="933d5-114">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="933d5-115">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="933d5-115">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="933d5-116">Popisuje některé osvědčené postupy pro vytváření spolehlivé aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="933d5-116">Describes some of the best practices for creating reliable .NET applications.</span></span> <span data-ttu-id="933d5-117">Tato část je určen pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="933d5-117">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="933d5-118">Pokyny pro zabezpečení nespravovaného kódu</span><span class="sxs-lookup"><span data-stu-id="933d5-118">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="933d5-119">Popisuje některé osvědčené postupy a aspekty zabezpečení při volání nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="933d5-119">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="933d5-120">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="933d5-120">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="933d5-121">Popisuje, jak můžete implementovat na základě deklarace identity ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="933d5-121">Describes how you can implement claims-based identity in your applications.</span></span>  

<span data-ttu-id="933d5-122">[Změny zabezpečení](../../../docs/framework/security/security-changes.md) popisuje důležité změny v systému zabezpečení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="933d5-122">[Security Changes](../../../docs/framework/security/security-changes.md) Describes important changes to the .NET Framework security system.</span></span>

## <a name="related-sections"></a><span data-ttu-id="933d5-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="933d5-123">Related Sections</span></span>  
 [<span data-ttu-id="933d5-124">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="933d5-124">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="933d5-125">Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.</span><span class="sxs-lookup"><span data-stu-id="933d5-125">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
