---
title: Změny zabezpečení v rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61f9e68bcc554dc3e4a4878e575d3f046a8ef9f5
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378590"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="c9683-102">Změny zabezpečení v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c9683-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="c9683-103">Nejdůležitější změny zabezpečení v rozhraní .NET Framework 4.5 je v silné názvy.</span><span class="sxs-lookup"><span data-stu-id="c9683-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="c9683-104">Zobrazit [vylepšené silné názvy](../../../docs/framework/app-domains/enhanced-strong-naming.md) popis těchto změn.</span><span class="sxs-lookup"><span data-stu-id="c9683-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="c9683-105">Rozhraní .NET Framework poskytuje model zabezpečení dvouvrstvé pro spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9683-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] <span data-ttu-id="c9683-106">spuštění aplikace v kontejneru Windows zabezpečení, která omezuje přístup k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="c9683-106">apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="c9683-107">V rámci kontejneru spusťte spravované aplikace plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="c9683-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="c9683-108">Z hlediska kódu access security (CAS) není nic, co Vývojář můžete udělat ke zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c9683-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="c9683-109">Informace o oprávněních udělených systémem Windows, naleznete v tématu [deklarace funkcí aplikace (aplikace pro Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="c9683-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="c9683-110">Informace o vytváření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, najdete v článku [vytvoření první aplikace pro Windows Store pomocí jazyka C# nebo Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="c9683-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
