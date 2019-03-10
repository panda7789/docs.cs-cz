---
title: Windows Forms – zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: f64d5ef2e9bb0e977b4c007e8c5109ac0c331a84
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709546"
---
# <a name="windows-forms-security"></a><span data-ttu-id="b29fe-102">Windows Forms – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b29fe-102">Windows Forms Security</span></span>
<span data-ttu-id="b29fe-103">Windows Forms obsahuje model zabezpečení, který je založený na kódu (zabezpečení, které úrovně jsou nastavené pro kód, bez ohledu na to, uživatel, který spouští kód).</span><span class="sxs-lookup"><span data-stu-id="b29fe-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="b29fe-104">To je ještě jakékoli schémata zabezpečení, které mohou být v místě již v počítači.</span><span class="sxs-lookup"><span data-stu-id="b29fe-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="b29fe-105">Může jít o jazyku prohlížeče (například v zóně zabezpečení na základě dostupné v aplikaci Internet Explorer) nebo operačního systému (například zabezpečení na základě přihlašovacích údajů systému Windows NT).</span><span class="sxs-lookup"><span data-stu-id="b29fe-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b29fe-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b29fe-106">In This Section</span></span>  
 [<span data-ttu-id="b29fe-107">Přehled zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b29fe-107">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)  
 <span data-ttu-id="b29fe-108">Stručnosti vysvětluje, že model zabezpečení rozhraní .NET Framework a základní kroky nezbytné k zajištění formulářů Windows ve vaší aplikaci jsou v bezpečí.</span><span class="sxs-lookup"><span data-stu-id="b29fe-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="b29fe-109">Zabezpečenější přístup k souborům a datům ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b29fe-109">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="b29fe-110">Popisuje, jak získat přístup k souborům a datům v částečně důvěryhodném prostředí.</span><span class="sxs-lookup"><span data-stu-id="b29fe-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="b29fe-111">Zabezpečenější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b29fe-111">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="b29fe-112">Popisuje, jak získat přístup k funkcím tisku v prostředí částečně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="b29fe-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="b29fe-113">Dodatečné informace o zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b29fe-113">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="b29fe-114">Popisuje provádění manipulaci s okna, použití schránky a volání nespravovaného kódu v částečně důvěryhodném prostředí.</span><span class="sxs-lookup"><span data-stu-id="b29fe-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b29fe-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b29fe-115">Related Sections</span></span>  
 <span data-ttu-id="b29fe-116">[Výchozí zásady zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b29fe-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="b29fe-117">Obsahuje seznam výchozích oprávnění udělené v sady oprávnění plné důvěryhodnosti, místní Intranet a Internet.</span><span class="sxs-lookup"><span data-stu-id="b29fe-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="b29fe-118">[Správa obecných zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b29fe-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="b29fe-119">Poskytuje informace o správě zásad zabezpečení rozhraní .NET Framework a zvyšování oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b29fe-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="b29fe-120">Správa nebezpečných oprávnění a zásad</span><span class="sxs-lookup"><span data-stu-id="b29fe-120">Dangerous Permissions and Policy Administration</span></span>](../misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="b29fe-121">Tento článek popisuje některé z rozhraní.NET Framework oprávnění, která by případně mohla být požadavky zabezpečení systému.</span><span class="sxs-lookup"><span data-stu-id="b29fe-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="b29fe-122">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="b29fe-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="b29fe-123">Obsahuje odkazy na témata, která popisují doporučené postupy pro bezpečné psaní kódu pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b29fe-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="b29fe-124">[Vyžadování oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b29fe-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="b29fe-125">Popisuje způsob používání atributů, které umožní modulu runtime vědět, jaká oprávnění potřebuje váš kód ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="b29fe-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="b29fe-126">Klíčové koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b29fe-126">Key Security Concepts</span></span>](../../standard/security/key-security-concepts.md)  
 <span data-ttu-id="b29fe-127">Obsahuje odkazy na témata, které pokrývají základní aspekty zabezpečení kódu.</span><span class="sxs-lookup"><span data-stu-id="b29fe-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="b29fe-128">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="b29fe-128">Code Access Security Basics</span></span>](../misc/code-access-security-basics.md)  
 <span data-ttu-id="b29fe-129">Tento článek popisuje základní informace o práci s rozhraním .NET Framework spustit čas zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b29fe-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="b29fe-130">[Určení, kdy chcete zásadu zabezpečení upravit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b29fe-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="b29fe-131">Vysvětluje, jak zjistit, když vaše aplikace potřebuje odchýlení od výchozí zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b29fe-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="b29fe-132">[Nasazení zásady zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b29fe-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="b29fe-133">Tento článek popisuje nejlepší způsob nasazení změny zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b29fe-133">Discusses the best manner for deploying security policy changes.</span></span>
