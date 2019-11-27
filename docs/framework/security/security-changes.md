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
ms.openlocfilehash: af2869e5ca3b41778c094b7a78a9493e74868811
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204496"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="83e11-102">Změny zabezpečení v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="83e11-102">Security Changes in the .NET Framework</span></span>

<span data-ttu-id="83e11-103">Nejdůležitější změnou zabezpečení v .NET Framework 4,5 je vytváření silných názvů.</span><span class="sxs-lookup"><span data-stu-id="83e11-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="83e11-104">Popis těchto změn najdete v tématu [Rozšířené silné pojmenování](../../standard/assembly/enhanced-strong-naming.md) .</span><span class="sxs-lookup"><span data-stu-id="83e11-104">See [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
<span data-ttu-id="83e11-105">.NET Framework poskytuje model zabezpečení se dvěma vrstvami pro spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="83e11-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> <span data-ttu-id="83e11-106">Aplikace Windows 8. x ze Storu běží v kontejneru zabezpečení systému Windows, který omezuje přístup k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="83e11-106">Windows 8.x Store apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="83e11-107">V rámci tohoto kontejneru běží spravované aplikace s plnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="83e11-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="83e11-108">V perspektivě zabezpečení přístupu kódu (CAS) není k dispozici žádný vývojář, který by mohl zvýšit oprávnění.</span><span class="sxs-lookup"><span data-stu-id="83e11-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="83e11-109">Informace o oprávněních udělených systémem Windows najdete v tématu [deklarace schopností aplikace (aplikace pro Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) na stránce Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="83e11-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="83e11-110">Informace o vytvoření aplikace Windows 8. x Store najdete v tématu [Vytvoření první aplikace pro C# Windows store pomocí nebo Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="83e11-110">For information about creating a Windows 8.x Store app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
