---
title: "Postupy: Odstranění klíče z registru v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cb98c02531bac133b9dc37a92f75d5c0418dc7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="eee08-102">Postupy: Odstranění klíče z registru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eee08-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="eee08-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> a <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> metody slouží k odstranění klíče registru.</span><span class="sxs-lookup"><span data-stu-id="eee08-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="eee08-104">Postup</span><span class="sxs-lookup"><span data-stu-id="eee08-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="eee08-105">Chcete-li odstranit klíč registru</span><span class="sxs-lookup"><span data-stu-id="eee08-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="eee08-106">Použití `DeleteSubKey` metodu za účelem odstranění klíče z registru.</span><span class="sxs-lookup"><span data-stu-id="eee08-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="eee08-107">Tento příklad odstraní klíče Software/TestApp v podregistru CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="eee08-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="eee08-108">Můžete to změnit v kódu na příslušným řetězcem nebo vycházet z informací zadaných uživatelem.</span><span class="sxs-lookup"><span data-stu-id="eee08-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="eee08-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="eee08-109">Robust Programming</span></span>  
 <span data-ttu-id="eee08-110">`DeleteSubKey` Metoda vrátí prázdný řetězec, pokud neexistuje dvojice klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="eee08-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="eee08-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="eee08-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="eee08-112">Název klíče je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="eee08-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="eee08-113">Uživatel nemá oprávnění k odstranění klíče registru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="eee08-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="eee08-114">Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="eee08-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="eee08-115">Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="eee08-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="eee08-116">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="eee08-116">.NET Framework Security</span></span>  
 <span data-ttu-id="eee08-117">Volání registrů se nezdaří, pokud nejsou udělena buď dostatečná oprávnění pro spuštění (<xref:System.Security.Permissions.RegistryPermission>) nebo pokud uživatel nemá správný přístup (jako seznamy ACL) pro vytvoření nebo zápis k nastavení.</span><span class="sxs-lookup"><span data-stu-id="eee08-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="eee08-118">Například místní aplikace, který má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="eee08-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee08-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="eee08-119">See Also</span></span>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey>  
 [<span data-ttu-id="eee08-120">Zabezpečení a registr</span><span class="sxs-lookup"><span data-stu-id="eee08-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 [<span data-ttu-id="eee08-121">Čtení a zápis do registru</span><span class="sxs-lookup"><span data-stu-id="eee08-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
