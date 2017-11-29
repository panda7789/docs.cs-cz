---
title: "Zabezpečení v rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, security
- security [.NET Framework], about security
- application development [.NET Framework], security
- security [.NET Framework]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
caps.latest.revision: "37"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5d6bf5929466d09b70cb74ffdf6c46d21c6f85ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-in-the-net-framework"></a><span data-ttu-id="3ffd1-102">Zabezpečení v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ffd1-102">Security in the .NET Framework</span></span>
<span data-ttu-id="3ffd1-103">Modul common language runtime a rozhraní .NET Framework poskytují mnoho užitečných tříd a služby, které umožňuje vývojářům snadno psát kód, zabezpečení a umožňují správcům systému přizpůsobit oprávnění udělená kódu tak, aby měl přístup chráněné zdroje.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-103">The common language runtime and the .NET Framework provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="3ffd1-104">Kromě toho modul runtime a rozhraní .NET Framework poskytují užitečné třídy a služby, které usnadňují použití kryptografie a na základě rolí zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-104">In addition, the runtime and the .NET Framework provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ffd1-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3ffd1-105">In This Section</span></span>  
 [<span data-ttu-id="3ffd1-106">Změny zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3ffd1-106">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)  
 <span data-ttu-id="3ffd1-107">Popisuje důležité změny v systému zabezpečení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-107">Describes important changes to the .NET Framework security system.</span></span>  
  
 [<span data-ttu-id="3ffd1-108">Klíčové koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3ffd1-108">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="3ffd1-109">Obsahuje přehled common language runtime funkce zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-109">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="3ffd1-110">Tato část je určen pro vývojáře a správce systému.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-110">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="3ffd1-111">Na základě rolí zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3ffd1-111">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="3ffd1-112">Popisuje, jak pracovat se zabezpečením na základě rolí v kódu.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-112">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="3ffd1-113">Tato část je určen pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-113">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="3ffd1-114">Kryptografický Model</span><span class="sxs-lookup"><span data-stu-id="3ffd1-114">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="3ffd1-115">Poskytuje přehled kryptografických služeb rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-115">Provides an overview of cryptographic services provided by the .NET Framework.</span></span> <span data-ttu-id="3ffd1-116">Tato část je určen pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-116">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="3ffd1-117">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="3ffd1-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="3ffd1-118">Popisuje některé osvědčené postupy pro vytváření spolehlivých aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-118">Describes some of the best practices for creating reliable .NET Framework applications.</span></span> <span data-ttu-id="3ffd1-119">Tato část je určen pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-119">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="3ffd1-120">Pokyny pro zabezpečení nespravovaného kódu</span><span class="sxs-lookup"><span data-stu-id="3ffd1-120">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="3ffd1-121">Popisuje některé osvědčené postupy a aspekty zabezpečení při volání nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-121">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="3ffd1-122">Technologie Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="3ffd1-122">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="3ffd1-123">Popisuje, jak můžete implementovat na základě deklarace identity ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-123">Describes how you can implement claims-based identity in your applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3ffd1-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3ffd1-124">Related Sections</span></span>  
 [<span data-ttu-id="3ffd1-125">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="3ffd1-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="3ffd1-126">Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.</span><span class="sxs-lookup"><span data-stu-id="3ffd1-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
