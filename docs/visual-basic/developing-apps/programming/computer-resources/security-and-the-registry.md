---
title: Zabezpečení a registr
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345484"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="c6dcb-102">Zabezpečení a registr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6dcb-102">Security and the Registry (Visual Basic)</span></span>

<span data-ttu-id="c6dcb-103">Tato stránka popisuje důsledky zabezpečení ukládání dat do registru.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="c6dcb-104">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="c6dcb-104">Permissions</span></span>  

 <span data-ttu-id="c6dcb-105">Není bezpečné ukládat tajné klíče, jako jsou hesla, v registru jako prostý text, a to i v případě, že je klíč registru chráněný pomocí seznamů řízení přístupu (ACL).</span><span class="sxs-lookup"><span data-stu-id="c6dcb-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="c6dcb-106">Práce s registrem může ohrozit zabezpečení tím, že umožňuje nevhodný přístup k systémovým prostředkům nebo chráněným informacím.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="c6dcb-107">Chcete-li použít tyto vlastnosti, musíte mít oprávnění ke čtení a zápisu z výčtu <xref:System.Security.Permissions.RegistryPermissionAccess>, který řídí přístup k proměnným registru.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="c6dcb-108">Veškerý kód spuštěný s úplným vztahem důvěryhodnosti (pod výchozí zásadou zabezpečení je to jakýkoli kód nainstalovaný na místním pevném disku uživatele) má potřebná oprávnění pro přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="c6dcb-109">Další informace naleznete v tématu <xref:System.Security.Permissions.RegistryPermission> Class.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="c6dcb-110">Proměnné registru by neměly být uloženy v umístěních paměti, kde k nim má přístup kód bez <xref:System.Security.Permissions.RegistryPermission>.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="c6dcb-111">Podobně při udělování oprávnění udělte minimální oprávnění potřebná k provedení úlohy.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="c6dcb-112">Hodnoty přístupu k oprávněním registru jsou definovány výčtem <xref:System.Security.Permissions.RegistryPermissionAccess>.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="c6dcb-113">Následující tabulka podrobně popisuje její členy.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="c6dcb-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c6dcb-114">Value</span></span>|<span data-ttu-id="c6dcb-115">Přístup k proměnným registru</span><span class="sxs-lookup"><span data-stu-id="c6dcb-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="c6dcb-116">Vytváření, čtení a zápis</span><span class="sxs-lookup"><span data-stu-id="c6dcb-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="c6dcb-117">Create</span><span class="sxs-lookup"><span data-stu-id="c6dcb-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="c6dcb-118">Bez přístupu</span><span class="sxs-lookup"><span data-stu-id="c6dcb-118">No access</span></span>|  
|`Read`|<span data-ttu-id="c6dcb-119">Pro čtení</span><span class="sxs-lookup"><span data-stu-id="c6dcb-119">Read</span></span>|  
|`Write`|<span data-ttu-id="c6dcb-120">Zapisovat</span><span class="sxs-lookup"><span data-stu-id="c6dcb-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="c6dcb-121">Kontrola hodnot v klíčích registru</span><span class="sxs-lookup"><span data-stu-id="c6dcb-121">Checking Values in Registry Keys</span></span>  

 <span data-ttu-id="c6dcb-122">Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tato hodnota již existuje.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="c6dcb-123">Jiný proces, pravděpodobně škodlivý, již mohl vytvořit hodnotu a mít k ní přístup.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="c6dcb-124">Při vložení dat do hodnoty registru jsou data k dispozici pro druhý proces.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="c6dcb-125">Chcete-li tomu zabránit, použijte metodu `GetValue`.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="c6dcb-126">Vrátí `Nothing`, pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c6dcb-127">Při čtení registru z webové aplikace závisí identita aktuálního uživatele na ověřování a zosobnění implementovaného ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c6dcb-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6dcb-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6dcb-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="c6dcb-129">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="c6dcb-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
