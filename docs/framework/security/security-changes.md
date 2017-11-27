---
title: "Změny zabezpečení v rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
caps.latest.revision: "52"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c1a96e30527aa3da4274ed55059b24aa5a7eeb47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="a0a3e-102">Změny zabezpečení v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a0a3e-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="a0a3e-103">Nejdůležitější změny zabezpečení v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] v silné názvy.</span><span class="sxs-lookup"><span data-stu-id="a0a3e-103">The most important change to security in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is in strong naming.</span></span> <span data-ttu-id="a0a3e-104">V tématu [rozšířené silné názvy](../../../docs/framework/app-domains/enhanced-strong-naming.md) popis tyto změny.</span><span class="sxs-lookup"><span data-stu-id="a0a3e-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="a0a3e-105">Rozhraní .NET Framework poskytuje model zabezpečení dvouvrstvá pro spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0a3e-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]<span data-ttu-id="a0a3e-106">aplikace běžet v kontejneru zabezpečení systému Windows, která omezuje přístup k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="a0a3e-106"> apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="a0a3e-107">V rámci kontejneru spusťte plně důvěryhodný pro spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0a3e-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="a0a3e-108">Z hlediska zabezpečení (CA) kód přístup není nic, které vývojář může provádět o zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="a0a3e-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="a0a3e-109">Informace o oprávnění udělují Windows najdete v tématu [deklarace funkce aplikace (aplikace pro Windows Store)](http://go.microsoft.com/fwlink/?LinkId=230436) ve službě Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="a0a3e-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](http://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="a0a3e-110">Informace o vytváření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, najdete v části [vytvoření první aplikace Windows Store pomocí jazyka C# nebo Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="a0a3e-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
