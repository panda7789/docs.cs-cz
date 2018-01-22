---
title: "Windows Forms – zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8bd9b87fdfa54a6f9bf53e4fa897106257b4c625
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="windows-forms-security"></a><span data-ttu-id="c002a-102">Windows Forms – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c002a-102">Windows Forms Security</span></span>
<span data-ttu-id="c002a-103">Windows Forms funkce model zabezpečení, které je založené na kódu (zabezpečení, které úrovně jsou nastavené na kód, bez ohledu na to uživatel, který spouští kód).</span><span class="sxs-lookup"><span data-stu-id="c002a-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="c002a-104">Toto je kromě všech schémata zabezpečení, které mohou být v místě již v systému.</span><span class="sxs-lookup"><span data-stu-id="c002a-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="c002a-105">Může jít o programů v prohlížeče (například na základě zóny zabezpečení k dispozici v aplikaci Internet Explorer) nebo operačního systému (například zabezpečení na základě přihlašovacích údajů systému Windows NT).</span><span class="sxs-lookup"><span data-stu-id="c002a-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c002a-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c002a-106">In This Section</span></span>  
 [<span data-ttu-id="c002a-107">Přehled zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c002a-107">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 <span data-ttu-id="c002a-108">Stručně popisuje model zabezpečení rozhraní .NET Framework a základními kroky, které jsou nezbytné pro zajištění Windows Forms v aplikaci jsou zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="c002a-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="c002a-109">Zabezpečenější přístup k souborům a datům ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c002a-109">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="c002a-110">Popisuje, jak přístup k souborům a data v prostředí s polovičním důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="c002a-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="c002a-111">Zabezpečenější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c002a-111">More Secure Printing in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="c002a-112">Popisuje, jak chcete dostat ke službám tisku v prostředí s polovičním důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="c002a-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="c002a-113">Dodatečné informace o zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c002a-113">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="c002a-114">Popisuje provádění okno manipulaci, použití schránky a volání nespravovaného kódu v prostředí s polovičním důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="c002a-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c002a-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c002a-115">Related Sections</span></span>  
 [<span data-ttu-id="c002a-116">NIB: Výchozí zásady zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c002a-116">NIB: Default Security Policy</span></span>](http://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 <span data-ttu-id="c002a-117">Uvádí výchozí oprávnění udělená oprávnění sad úplný vztah důvěryhodnosti, místního intranetu a Internetu.</span><span class="sxs-lookup"><span data-stu-id="c002a-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 [<span data-ttu-id="c002a-118">NIB: Správa obecných zásad zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c002a-118">NIB: General Security Policy Administration</span></span>](http://msdn.microsoft.com/library/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 <span data-ttu-id="c002a-119">Poskytuje informace o správě zásad zabezpečení rozhraní .NET Framework a zvyšování oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c002a-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="c002a-120">Správa nebezpečných oprávnění a zásad</span><span class="sxs-lookup"><span data-stu-id="c002a-120">Dangerous Permissions and Policy Administration</span></span>](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="c002a-121">Popisuje některé z rozhraní.NET Framework oprávnění, která může potenciálně povolit zabezpečení systému možné obejít.</span><span class="sxs-lookup"><span data-stu-id="c002a-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="c002a-122">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="c002a-122">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="c002a-123">Odkazy na témata, které popisují doporučené postupy pro bezpečné psaní kódu pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c002a-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 [<span data-ttu-id="c002a-124">NIB: Vyžadování oprávnění</span><span class="sxs-lookup"><span data-stu-id="c002a-124">NIB: Requesting Permissions</span></span>](http://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 <span data-ttu-id="c002a-125">Popisuje použití atributů, které chcete dát modulu runtime vědět, jaká oprávnění kódu je potřeba spustit.</span><span class="sxs-lookup"><span data-stu-id="c002a-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="c002a-126">Klíčové koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c002a-126">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="c002a-127">Odkazy na témata, které se týkají základní aspekty zabezpečení kódu.</span><span class="sxs-lookup"><span data-stu-id="c002a-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="c002a-128">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="c002a-128">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 <span data-ttu-id="c002a-129">Popisuje základní informace o práci s rozhraním .NET Framework spustit čas zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c002a-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 [<span data-ttu-id="c002a-130">NIB: Určení, kdy upravit zásady zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c002a-130">NIB: Determining When to Modify Security Policy</span></span>](http://msdn.microsoft.com/library/af749b17-e461-409d-84b9-a3d44789db16)  
 <span data-ttu-id="c002a-131">Vysvětluje, jak k určení, kdy aplikace potřebují vycházející z výchozí zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c002a-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 [<span data-ttu-id="c002a-132">NIB: Nasazení zásad zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c002a-132">NIB: Deploying Security Policy</span></span>](http://msdn.microsoft.com/library/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 <span data-ttu-id="c002a-133">Popisuje nejlepší způsob pro nasazení změny zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c002a-133">Discusses the best manner for deploying security policy changes.</span></span>
