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
ms.openlocfilehash: 0c3c7eb20bb3368205dab4c7e03b6b80d09a2121
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775275"
---
# <a name="security-in-net"></a><span data-ttu-id="399d2-102">Zabezpečení v .NET</span><span class="sxs-lookup"><span data-stu-id="399d2-102">Security in .NET</span></span>

<span data-ttu-id="399d2-103">Modul CLR (Common Language Runtime) a .NET poskytují spoustu užitečných tříd a služeb, které vývojářům umožňují snadno napsat zabezpečený kód a umožnit správcům systému přizpůsobit oprávnění udělená kódu, aby mohl přistupovat k chráněným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="399d2-103">The common language runtime and the .NET provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="399d2-104">Kromě toho modul runtime a rozhraní .NET poskytují užitečné třídy a služby, které usnadňují použití kryptografie a zabezpečení založeného na rolích.</span><span class="sxs-lookup"><span data-stu-id="399d2-104">In addition, the runtime and the .NET provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="399d2-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="399d2-105">In this section</span></span>

- [<span data-ttu-id="399d2-106">Klíčové koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="399d2-106">Key Security Concepts</span></span>](key-security-concepts.md)  
<span data-ttu-id="399d2-107">Poskytuje přehled funkcí zabezpečení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="399d2-107">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="399d2-108">Tato část je zajímavá pro vývojáře a správce systému.</span><span class="sxs-lookup"><span data-stu-id="399d2-108">This section is of interest to developers and system administrators.</span></span>

- [<span data-ttu-id="399d2-109">Zabezpečení na základě rolí</span><span class="sxs-lookup"><span data-stu-id="399d2-109">Role-Based Security</span></span>](role-based-security.md)  
<span data-ttu-id="399d2-110">Popisuje, jak v kódu pracovat se zabezpečením na základě rolí.</span><span class="sxs-lookup"><span data-stu-id="399d2-110">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="399d2-111">Tato část je zajímavá pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="399d2-111">This section is of interest to developers.</span></span>

- [<span data-ttu-id="399d2-112">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="399d2-112">Cryptography Model</span></span>](cryptography-model.md)  
<span data-ttu-id="399d2-113">Poskytuje přehled kryptografických služeb poskytovaných .NET.</span><span class="sxs-lookup"><span data-stu-id="399d2-113">Provides an overview of cryptographic services provided by .NET.</span></span> <span data-ttu-id="399d2-114">Tato část je zajímavá pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="399d2-114">This section is of interest to developers.</span></span>

- [<span data-ttu-id="399d2-115">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="399d2-115">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)  
<span data-ttu-id="399d2-116">Popisuje některé z osvědčených postupů pro vytváření spolehlivých aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="399d2-116">Describes some of the best practices for creating reliable .NET applications.</span></span> <span data-ttu-id="399d2-117">Tato část je zajímavá pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="399d2-117">This section is of interest to developers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="399d2-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="399d2-118">Related sections</span></span>

[<span data-ttu-id="399d2-119">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="399d2-119">Development Guide</span></span>](../../framework/development-guide.md)  
<span data-ttu-id="399d2-120">Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.</span><span class="sxs-lookup"><span data-stu-id="399d2-120">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
