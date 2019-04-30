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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799369"
---
# <a name="windows-forms-security"></a><span data-ttu-id="44255-102">Windows Forms – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="44255-102">Windows Forms Security</span></span>
<span data-ttu-id="44255-103">Windows Forms obsahuje model zabezpečení, který je založený na kódu (zabezpečení, které úrovně jsou nastavené pro kód, bez ohledu na to, uživatel, který spouští kód).</span><span class="sxs-lookup"><span data-stu-id="44255-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="44255-104">To je ještě jakékoli schémata zabezpečení, které mohou být v místě již v počítači.</span><span class="sxs-lookup"><span data-stu-id="44255-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="44255-105">Může jít o jazyku prohlížeče (například v zóně zabezpečení na základě dostupné v aplikaci Internet Explorer) nebo operačního systému (například zabezpečení na základě přihlašovacích údajů systému Windows NT).</span><span class="sxs-lookup"><span data-stu-id="44255-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44255-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="44255-106">In This Section</span></span>  
 [<span data-ttu-id="44255-107">Přehled zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44255-107">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)  
 <span data-ttu-id="44255-108">Stručnosti vysvětluje, že model zabezpečení rozhraní .NET Framework a základní kroky nezbytné k zajištění formulářů Windows ve vaší aplikaci jsou v bezpečí.</span><span class="sxs-lookup"><span data-stu-id="44255-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="44255-109">Zabezpečenější přístup k souborům a datům ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44255-109">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="44255-110">Popisuje, jak získat přístup k souborům a datům v částečně důvěryhodném prostředí.</span><span class="sxs-lookup"><span data-stu-id="44255-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="44255-111">Zabezpečenější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44255-111">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="44255-112">Popisuje, jak získat přístup k funkcím tisku v prostředí částečně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="44255-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="44255-113">Dodatečné informace o zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44255-113">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="44255-114">Popisuje provádění manipulaci s okna, použití schránky a volání nespravovaného kódu v částečně důvěryhodném prostředí.</span><span class="sxs-lookup"><span data-stu-id="44255-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="44255-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="44255-115">Related Sections</span></span>  
 <span data-ttu-id="44255-116">[Výchozí zásady zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="44255-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="44255-117">Obsahuje seznam výchozích oprávnění udělené v sady oprávnění plné důvěryhodnosti, místní Intranet a Internet.</span><span class="sxs-lookup"><span data-stu-id="44255-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="44255-118">[Správa obecných zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="44255-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="44255-119">Poskytuje informace o správě zásad zabezpečení rozhraní .NET Framework a zvyšování oprávnění.</span><span class="sxs-lookup"><span data-stu-id="44255-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="44255-120">Správa nebezpečných oprávnění a zásad</span><span class="sxs-lookup"><span data-stu-id="44255-120">Dangerous Permissions and Policy Administration</span></span>](../misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="44255-121">Tento článek popisuje některé z rozhraní.NET Framework oprávnění, která by případně mohla být požadavky zabezpečení systému.</span><span class="sxs-lookup"><span data-stu-id="44255-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="44255-122">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="44255-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="44255-123">Obsahuje odkazy na témata, která popisují doporučené postupy pro bezpečné psaní kódu pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44255-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="44255-124">[Vyžadování oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="44255-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="44255-125">Popisuje způsob používání atributů, které umožní modulu runtime vědět, jaká oprávnění potřebuje váš kód ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="44255-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="44255-126">Klíčové koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="44255-126">Key Security Concepts</span></span>](../../standard/security/key-security-concepts.md)  
 <span data-ttu-id="44255-127">Obsahuje odkazy na témata, které pokrývají základní aspekty zabezpečení kódu.</span><span class="sxs-lookup"><span data-stu-id="44255-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="44255-128">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="44255-128">Code Access Security Basics</span></span>](../misc/code-access-security-basics.md)  
 <span data-ttu-id="44255-129">Tento článek popisuje základní informace o práci s rozhraním .NET Framework spustit čas zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="44255-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="44255-130">[Určení, kdy chcete zásadu zabezpečení upravit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="44255-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="44255-131">Vysvětluje, jak zjistit, když vaše aplikace potřebuje odchýlení od výchozí zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="44255-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="44255-132">[Nasazení zásady zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="44255-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="44255-133">Tento článek popisuje nejlepší způsob nasazení změny zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="44255-133">Discusses the best manner for deploying security policy changes.</span></span>
