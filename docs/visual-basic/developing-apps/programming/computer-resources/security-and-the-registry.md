---
title: "Zabezpečení a registr (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0961d21417cbb5efcd9f38112c4e8ecb393faccd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="ba2a7-102">Zabezpečení a registr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba2a7-102">Security and the Registry (Visual Basic)</span></span>
<span data-ttu-id="ba2a7-103">Tato stránka popisuje bezpečnostních důsledcích ukládání dat v registru.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="ba2a7-104">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="ba2a7-104">Permissions</span></span>  
 <span data-ttu-id="ba2a7-105">Není bezpečné uchovávat tajné údaje, jako jsou hesla, v registru jako prostý text, i v případě, že je klíč registru chráněn pomocí seznamů řízení přístupu (seznamy řízení přístupu).</span><span class="sxs-lookup"><span data-stu-id="ba2a7-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="ba2a7-106">Práce s registrem může ohrozit zabezpečení tím, že nevhodný přístup k systémovým prostředkům nebo chráněný informace.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="ba2a7-107">Pokud chcete použít tyto vlastnosti, musí mít oprávnění z čtení a zápisu <xref:System.Security.Permissions.RegistryPermissionAccess> výčtu, která řídí přístup k registru proměnné.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="ba2a7-108">Jakýkoli kód spuštěn s úplným vztahem důvěryhodnosti (v části výchozí zásady zabezpečení, je to žádný kód nainstalována na místní pevný disk uživatele) musí mít potřebná oprávnění pro přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="ba2a7-109">Další informace najdete v tématu <xref:System.Security.Permissions.RegistryPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="ba2a7-110">Proměnné registru by neměly být uloženy v umístění v paměti kde code bez <xref:System.Security.Permissions.RegistryPermission> k nim měli přístup.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="ba2a7-111">Podobně při udělování oprávnění, udělte minimální oprávnění potřebná k provedení úlohy.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="ba2a7-112">Oprávnění k registrům jsou definovány <xref:System.Security.Permissions.RegistryPermissionAccess> výčtu.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="ba2a7-113">Následující tabulka uvádí její členy.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="ba2a7-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ba2a7-114">Value</span></span>|<span data-ttu-id="ba2a7-115">Přístup k registru proměnné</span><span class="sxs-lookup"><span data-stu-id="ba2a7-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="ba2a7-116">Vytváření, čtení a zápis</span><span class="sxs-lookup"><span data-stu-id="ba2a7-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="ba2a7-117">Create</span><span class="sxs-lookup"><span data-stu-id="ba2a7-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="ba2a7-118">Žádný přístup</span><span class="sxs-lookup"><span data-stu-id="ba2a7-118">No access</span></span>|  
|`Read`|<span data-ttu-id="ba2a7-119">Číst</span><span class="sxs-lookup"><span data-stu-id="ba2a7-119">Read</span></span>|  
|`Write`|<span data-ttu-id="ba2a7-120">Write</span><span class="sxs-lookup"><span data-stu-id="ba2a7-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="ba2a7-121">Kontrola hodnoty klíče registru</span><span class="sxs-lookup"><span data-stu-id="ba2a7-121">Checking Values in Registry Keys</span></span>  
 <span data-ttu-id="ba2a7-122">Když vytvoříte hodnotu registru, budete muset rozhodnout, co dělat v případě, že hodnota již existuje.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="ba2a7-123">Jiný proces, případně škodlivý jeden už možná máte vytvořené hodnota a mít přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="ba2a7-124">Když vložíte dat v hodnotě registru, data jsou k dispozici pro jiný proces.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="ba2a7-125">Chcete-li tomu zabránit, použijte `GetValue` metoda.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="ba2a7-126">Vrátí `Nothing` Pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba2a7-127">Při čtení registru z webové aplikace, identity aktuální uživatel závisí na ověřování a zosobnění implementována ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ba2a7-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba2a7-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba2a7-128">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [<span data-ttu-id="ba2a7-129">Čtení a zápis do registru</span><span class="sxs-lookup"><span data-stu-id="ba2a7-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
