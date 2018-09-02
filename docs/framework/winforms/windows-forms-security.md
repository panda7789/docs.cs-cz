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
ms.openlocfilehash: 75016e9e04cf47782add18c87f7c677931743a4e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397247"
---
# <a name="windows-forms-security"></a><span data-ttu-id="4be24-102">Windows Forms – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4be24-102">Windows Forms Security</span></span>
<span data-ttu-id="4be24-103">Windows Forms obsahuje model zabezpečení, který je založený na kódu (zabezpečení, které úrovně jsou nastavené pro kód, bez ohledu na to, uživatel, který spouští kód).</span><span class="sxs-lookup"><span data-stu-id="4be24-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="4be24-104">To je ještě jakékoli schémata zabezpečení, které mohou být v místě již v počítači.</span><span class="sxs-lookup"><span data-stu-id="4be24-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="4be24-105">Může jít o jazyku prohlížeče (například v zóně zabezpečení na základě dostupné v aplikaci Internet Explorer) nebo operačního systému (například zabezpečení na základě přihlašovacích údajů systému Windows NT).</span><span class="sxs-lookup"><span data-stu-id="4be24-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4be24-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4be24-106">In This Section</span></span>  
 [<span data-ttu-id="4be24-107">Přehled zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4be24-107">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 <span data-ttu-id="4be24-108">Stručnosti vysvětluje, že model zabezpečení rozhraní .NET Framework a základní kroky nezbytné k zajištění formulářů Windows ve vaší aplikaci jsou v bezpečí.</span><span class="sxs-lookup"><span data-stu-id="4be24-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="4be24-109">Zabezpečenější přístup k souborům a datům ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4be24-109">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="4be24-110">Popisuje, jak získat přístup k souborům a datům v částečně důvěryhodném prostředí.</span><span class="sxs-lookup"><span data-stu-id="4be24-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="4be24-111">Zabezpečenější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4be24-111">More Secure Printing in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="4be24-112">Popisuje, jak získat přístup k funkcím tisku v prostředí částečně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="4be24-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="4be24-113">Dodatečné informace o zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4be24-113">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="4be24-114">Popisuje provádění manipulaci s okna, použití schránky a volání nespravovaného kódu v částečně důvěryhodném prostředí.</span><span class="sxs-lookup"><span data-stu-id="4be24-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4be24-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4be24-115">Related Sections</span></span>  
 [<span data-ttu-id="4be24-116">NIB: Výchozí zásady zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4be24-116">NIB: Default Security Policy</span></span>](https://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 <span data-ttu-id="4be24-117">Obsahuje seznam výchozích oprávnění udělené v sady oprávnění plné důvěryhodnosti, místní Intranet a Internet.</span><span class="sxs-lookup"><span data-stu-id="4be24-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 [<span data-ttu-id="4be24-118">NIB: Správa zásad zabezpečení hlavní</span><span class="sxs-lookup"><span data-stu-id="4be24-118">NIB: General Security Policy Administration</span></span>](https://msdn.microsoft.com/library/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 <span data-ttu-id="4be24-119">Poskytuje informace o správě zásad zabezpečení rozhraní .NET Framework a zvyšování oprávnění.</span><span class="sxs-lookup"><span data-stu-id="4be24-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="4be24-120">Správa nebezpečných oprávnění a zásad</span><span class="sxs-lookup"><span data-stu-id="4be24-120">Dangerous Permissions and Policy Administration</span></span>](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="4be24-121">Tento článek popisuje některé z rozhraní.NET Framework oprávnění, která by případně mohla být požadavky zabezpečení systému.</span><span class="sxs-lookup"><span data-stu-id="4be24-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="4be24-122">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="4be24-122">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="4be24-123">Obsahuje odkazy na témata, která popisují doporučené postupy pro bezpečné psaní kódu pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4be24-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 [<span data-ttu-id="4be24-124">NIB: Vyžadování oprávnění</span><span class="sxs-lookup"><span data-stu-id="4be24-124">NIB: Requesting Permissions</span></span>](https://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 <span data-ttu-id="4be24-125">Popisuje způsob používání atributů, které umožní modulu runtime vědět, jaká oprávnění potřebuje váš kód ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="4be24-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="4be24-126">Klíčové koncepty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4be24-126">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="4be24-127">Obsahuje odkazy na témata, které pokrývají základní aspekty zabezpečení kódu.</span><span class="sxs-lookup"><span data-stu-id="4be24-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="4be24-128">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="4be24-128">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 <span data-ttu-id="4be24-129">Tento článek popisuje základní informace o práci s rozhraním .NET Framework spustit čas zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4be24-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 [<span data-ttu-id="4be24-130">NIB: Určení, kdy chcete zásadu zabezpečení upravit</span><span class="sxs-lookup"><span data-stu-id="4be24-130">NIB: Determining When to Modify Security Policy</span></span>](https://msdn.microsoft.com/library/af749b17-e461-409d-84b9-a3d44789db16)  
 <span data-ttu-id="4be24-131">Vysvětluje, jak zjistit, když vaše aplikace potřebuje odchýlení od výchozí zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4be24-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 [<span data-ttu-id="4be24-132">NIB: Nasazení zásad zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4be24-132">NIB: Deploying Security Policy</span></span>](https://msdn.microsoft.com/library/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 <span data-ttu-id="4be24-133">Tento článek popisuje nejlepší způsob nasazení změny zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4be24-133">Discusses the best manner for deploying security policy changes.</span></span>
