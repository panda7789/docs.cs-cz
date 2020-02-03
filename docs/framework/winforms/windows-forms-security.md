---
title: Zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: a3debf487b9b2a04277d9ce3007f28662fa4899e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734502"
---
# <a name="windows-forms-security"></a><span data-ttu-id="a0892-102">Windows Forms – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a0892-102">Windows Forms Security</span></span>
<span data-ttu-id="a0892-103">Model Windows Forms funkce je model zabezpečení, který je založen na kódu (úrovně zabezpečení jsou nastaveny pro kód bez ohledu na uživatele, který kód spustil).</span><span class="sxs-lookup"><span data-stu-id="a0892-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="a0892-104">To je navíc k jakýmkoli schématům zabezpečení, která mohou být již v systémovém systému zavedena.</span><span class="sxs-lookup"><span data-stu-id="a0892-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="a0892-105">Ty můžou zahrnovat ty v prohlížeči (například zabezpečení založené na zóně, které je dostupné v Internet Exploreru), nebo operační systém (třeba zabezpečení na základě přihlašovacích údajů systému Windows NT).</span><span class="sxs-lookup"><span data-stu-id="a0892-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0892-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a0892-106">In This Section</span></span>  
 [<span data-ttu-id="a0892-107">Přehled zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0892-107">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)  
 <span data-ttu-id="a0892-108">Stručně vysvětluje model zabezpečení .NET Framework a základní kroky nezbytné k zajištění zabezpečení model Windows Forms ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a0892-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="a0892-109">Zabezpečenější přístup k souborům a datům ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0892-109">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="a0892-110">Popisuje, jak získat přístup k souborům a datům v částečně důvěryhodném prostředí.</span><span class="sxs-lookup"><span data-stu-id="a0892-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="a0892-111">Zabezpečenější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0892-111">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="a0892-112">Popisuje, jak získat přístup k funkcím pro tisk v částečně důvěryhodném prostředí.</span><span class="sxs-lookup"><span data-stu-id="a0892-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="a0892-113">Dodatečné informace o zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0892-113">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="a0892-114">Popisuje provádění manipulace s oknem, použití schránky a volání nespravovaného kódu v částečně důvěryhodném prostředí.</span><span class="sxs-lookup"><span data-stu-id="a0892-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a0892-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a0892-115">Related Sections</span></span>  
 <span data-ttu-id="a0892-116">[Výchozí zásady zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a0892-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="a0892-117">Zobrazuje seznam výchozích oprávnění udělených v sadách oprávnění úplného vztahu důvěryhodnosti, místní intranet a Internet.</span><span class="sxs-lookup"><span data-stu-id="a0892-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="a0892-118">[Obecná Správa zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a0892-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="a0892-119">Poskytuje informace o správě .NET Framework zásad zabezpečení a zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="a0892-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="a0892-120">Nebezpečná oprávnění a Správa zásad</span><span class="sxs-lookup"><span data-stu-id="a0892-120">Dangerous Permissions and Policy Administration</span></span>](../misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="a0892-121">Popisuje některá oprávnění rozhraní the.NET Framework, která můžou potenciálně dovolit obejít bezpečnostnímu systému.</span><span class="sxs-lookup"><span data-stu-id="a0892-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="a0892-122">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="a0892-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="a0892-123">Obsahuje odkazy na témata, která vysvětlují osvědčené postupy pro bezpečné psaní kódu proti .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0892-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="a0892-124">[Žádosti o oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a0892-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="a0892-125">Popisuje použití atributů k umožnění modulu runtime, aby věděli, jaká oprávnění váš kód potřebují spustit.</span><span class="sxs-lookup"><span data-stu-id="a0892-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="a0892-126">Klíčové koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a0892-126">Key Security Concepts</span></span>](../../standard/security/key-security-concepts.md)  
 <span data-ttu-id="a0892-127">Obsahuje odkazy na témata, která se týkají základních aspektů zabezpečení kódu.</span><span class="sxs-lookup"><span data-stu-id="a0892-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="a0892-128">Základy zabezpečení přístupu ke kódu</span><span class="sxs-lookup"><span data-stu-id="a0892-128">Code Access Security Basics</span></span>](../misc/code-access-security-basics.md)  
 <span data-ttu-id="a0892-129">Popisuje základy práce se zásadami zabezpečení .NET Framework běhu.</span><span class="sxs-lookup"><span data-stu-id="a0892-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="a0892-130">[Určení, kdy se mají upravit zásady zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a0892-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="a0892-131">Vysvětluje, jak určit, kdy se aplikace musí odchýlit od výchozích zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a0892-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="a0892-132">[Nasazují se zásady zabezpečení.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a0892-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="a0892-133">Tento článek popisuje nejlepší způsob nasazení změn zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a0892-133">Discusses the best manner for deploying security policy changes.</span></span>
