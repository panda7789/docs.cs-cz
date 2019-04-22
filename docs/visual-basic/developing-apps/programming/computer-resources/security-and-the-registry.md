---
title: Zabezpečení a registr (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: dc0071d1fddf99bd712ebe8aea5c61bbc3522f93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839350"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="01b74-102">Zabezpečení a registr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01b74-102">Security and the Registry (Visual Basic)</span></span>
<span data-ttu-id="01b74-103">Tato stránka pojednává o bezpečnostních důsledcích ukládání dat do registru.</span><span class="sxs-lookup"><span data-stu-id="01b74-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="01b74-104">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="01b74-104">Permissions</span></span>  
 <span data-ttu-id="01b74-105">Není bezpečné uchovávat tajemství, jako jsou hesla, v registrech jako prostý text, i v případě, že klíč registru je chráněn pomocí ACL (seznamy řízení přístupu).</span><span class="sxs-lookup"><span data-stu-id="01b74-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="01b74-106">Práce s registrem může ohrozit zabezpečení tím, že nevhodný přístup k systémovým prostředkům nebo chráněné informace.</span><span class="sxs-lookup"><span data-stu-id="01b74-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="01b74-107">Použití těchto vlastností, musíte mít oprávnění z čtení a zápisu <xref:System.Security.Permissions.RegistryPermissionAccess> výčtu, které řídí přístup k proměnné registru.</span><span class="sxs-lookup"><span data-stu-id="01b74-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="01b74-108">Jakýkoli kód spuštěn s úplným vztahem důvěryhodnosti (podle výchozí zásady zabezpečení, je to žádný kód nainstalované na místním pevném disku uživatele) má potřebná oprávnění pro přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="01b74-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="01b74-109">Další informace najdete v tématu <xref:System.Security.Permissions.RegistryPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="01b74-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="01b74-110">Proměnné registru by neměly být uloženy v umístění v paměti kde kódu bez <xref:System.Security.Permissions.RegistryPermission> k nim přistupovat.</span><span class="sxs-lookup"><span data-stu-id="01b74-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="01b74-111">Podobně při udělování oprávnění udělte minimální oprávnění, které jsou nezbytné k dokončení práce.</span><span class="sxs-lookup"><span data-stu-id="01b74-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="01b74-112">Oprávnění k registrům, jsou určené <xref:System.Security.Permissions.RegistryPermissionAccess> výčtu.</span><span class="sxs-lookup"><span data-stu-id="01b74-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="01b74-113">Následující tabulka obsahuje podrobnosti o jejích členů.</span><span class="sxs-lookup"><span data-stu-id="01b74-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="01b74-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="01b74-114">Value</span></span>|<span data-ttu-id="01b74-115">Přístup k proměnné registru</span><span class="sxs-lookup"><span data-stu-id="01b74-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="01b74-116">Vytvoření, čtení a zápis</span><span class="sxs-lookup"><span data-stu-id="01b74-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="01b74-117">Create</span><span class="sxs-lookup"><span data-stu-id="01b74-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="01b74-118">Žádný přístup</span><span class="sxs-lookup"><span data-stu-id="01b74-118">No access</span></span>|  
|`Read`|<span data-ttu-id="01b74-119">Číst</span><span class="sxs-lookup"><span data-stu-id="01b74-119">Read</span></span>|  
|`Write`|<span data-ttu-id="01b74-120">Write</span><span class="sxs-lookup"><span data-stu-id="01b74-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="01b74-121">Kontroluje se hodnoty klíče registru</span><span class="sxs-lookup"><span data-stu-id="01b74-121">Checking Values in Registry Keys</span></span>  
 <span data-ttu-id="01b74-122">Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tuto hodnotu již existuje.</span><span class="sxs-lookup"><span data-stu-id="01b74-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="01b74-123">Jiný proces, možná škodlivý ten už možná máte vytvořené hodnotu a k ní máte přístup.</span><span class="sxs-lookup"><span data-stu-id="01b74-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="01b74-124">Když vkládáte data do hodnoty registru, data jsou k dispozici pro jiné procesy.</span><span class="sxs-lookup"><span data-stu-id="01b74-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="01b74-125">Chcete-li tomu zabránit, použijte `GetValue` metody.</span><span class="sxs-lookup"><span data-stu-id="01b74-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="01b74-126">Vrátí `Nothing` Pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="01b74-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="01b74-127">Při čtení registru z webové aplikace, identity aktuálního uživatele závisí na ověřování a zosobnění implementované ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="01b74-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b74-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01b74-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="01b74-129">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="01b74-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
