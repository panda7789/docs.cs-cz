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
ms.openlocfilehash: c62a469b3e31283e5790c747092a8fe504ef8c2a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47107906"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="572c2-102">Změny zabezpečení v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="572c2-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="572c2-103">Nejdůležitější změny zabezpečení v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] v silné názvy.</span><span class="sxs-lookup"><span data-stu-id="572c2-103">The most important change to security in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is in strong naming.</span></span> <span data-ttu-id="572c2-104">Zobrazit [vylepšené silné názvy](../../../docs/framework/app-domains/enhanced-strong-naming.md) popis těchto změn.</span><span class="sxs-lookup"><span data-stu-id="572c2-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="572c2-105">Rozhraní .NET Framework poskytuje model zabezpečení dvouvrstvé pro spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="572c2-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]<span data-ttu-id="572c2-106"> spuštění aplikace v kontejneru Windows zabezpečení, která omezuje přístup k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="572c2-106"> apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="572c2-107">V rámci kontejneru spusťte spravované aplikace plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="572c2-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="572c2-108">Z hlediska kódu access security (CAS) není nic, co Vývojář můžete udělat ke zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="572c2-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="572c2-109">Informace o oprávněních udělených systémem Windows, naleznete v tématu [deklarace funkcí aplikace (aplikace pro Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="572c2-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="572c2-110">Informace o vytváření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, najdete v článku [vytvoření první aplikace pro Windows Store pomocí jazyka C# nebo Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="572c2-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
