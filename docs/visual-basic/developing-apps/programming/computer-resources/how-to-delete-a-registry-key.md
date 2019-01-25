---
title: 'Postupy: Odstranění klíče z registru v jazyce Visual Basic'
ms.date: 07/20/2015
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
ms.openlocfilehash: 226dc22f42783bec11eb1ddc38f270477bb0fbab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633960"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="c2ad9-102">Postupy: Odstranění klíče z registru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2ad9-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="c2ad9-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> a <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> metody slouží k odstranění klíče registru.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="c2ad9-104">Postup</span><span class="sxs-lookup"><span data-stu-id="c2ad9-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="c2ad9-105">Odstranit klíč registru</span><span class="sxs-lookup"><span data-stu-id="c2ad9-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="c2ad9-106">Použití `DeleteSubKey` metodu k odstranění klíče z registru.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="c2ad9-107">Tento příklad odstraní klíč softwaru/TestApp v CurrentUser hive.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="c2ad9-108">Můžete změnit v kódu na odpovídající řetězec nebo vycházet z uživatelem zadané informace.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c2ad9-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c2ad9-109">Robust Programming</span></span>  
 <span data-ttu-id="c2ad9-110">`DeleteSubKey` Metoda vrátí prázdný řetězec, pokud je dvojice klíč/hodnota neexistuje.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="c2ad9-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="c2ad9-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c2ad9-112">Název klíče je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="c2ad9-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="c2ad9-113">Uživatel nemá oprávnění k odstranění klíče registru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="c2ad9-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="c2ad9-114">Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="c2ad9-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="c2ad9-115">Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="c2ad9-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c2ad9-116">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c2ad9-116">.NET Framework Security</span></span>  
 <span data-ttu-id="c2ad9-117">Volání registru selhat, pokud nejsou udělena buď dostatečná oprávnění za běhu (<xref:System.Security.Permissions.RegistryPermission>) nebo pokud uživatel nemá správný přístup (jako seznamy ACL) pro vytvoření nebo zápis do nastavení.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="c2ad9-118">Místní aplikace, který má oprávnění zabezpečení přístupu kódu například nemusí mít oprávnění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="c2ad9-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ad9-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2ad9-119">See also</span></span>
- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [<span data-ttu-id="c2ad9-120">Zabezpečení a registr</span><span class="sxs-lookup"><span data-stu-id="c2ad9-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [<span data-ttu-id="c2ad9-121">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="c2ad9-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
