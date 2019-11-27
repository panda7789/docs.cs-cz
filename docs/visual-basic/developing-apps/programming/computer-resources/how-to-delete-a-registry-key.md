---
title: 'Postupy: Odstranění klíče z registru'
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
ms.openlocfilehash: f38301a3a717a35b98e55804d6435d046bbbbab4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345644"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="6e813-102">Postupy: Odstranění klíče z registru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e813-102">How to: Delete a Registry Key in Visual Basic</span></span>

<span data-ttu-id="6e813-103">Metody <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> a <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> lze použít k odstranění klíčů registru.</span><span class="sxs-lookup"><span data-stu-id="6e813-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="6e813-104">Postup</span><span class="sxs-lookup"><span data-stu-id="6e813-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="6e813-105">Odstranění klíče registru</span><span class="sxs-lookup"><span data-stu-id="6e813-105">To delete a registry key</span></span>  
  
- <span data-ttu-id="6e813-106">Pomocí metody `DeleteSubKey` odstraňte klíč registru.</span><span class="sxs-lookup"><span data-stu-id="6e813-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="6e813-107">Tento příklad odstraní klíč Software/TestApp v podregistru CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6e813-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="6e813-108">Můžete to změnit v kódu na příslušný řetězec nebo se musí spoléhat na informace zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="6e813-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6e813-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6e813-109">Robust Programming</span></span>  

 <span data-ttu-id="6e813-110">Metoda `DeleteSubKey` vrátí prázdný řetězec, pokud dvojice klíč/hodnota neexistuje.</span><span class="sxs-lookup"><span data-stu-id="6e813-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="6e813-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="6e813-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6e813-112">Název klíče je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="6e813-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="6e813-113">Uživatel nemá oprávnění k odstranění klíčů registru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="6e813-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="6e813-114">Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="6e813-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="6e813-115">Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="6e813-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6e813-116">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6e813-116">.NET Framework Security</span></span>  

 <span data-ttu-id="6e813-117">Volání registru se nezdaří, pokud buď nejsou udělena dostatečná oprávnění za běhu (<xref:System.Security.Permissions.RegistryPermission>), nebo pokud uživatel nemá správný přístup (podle určení seznamů ACL) pro vytváření a zápis do nastavení.</span><span class="sxs-lookup"><span data-stu-id="6e813-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="6e813-118">Například místní aplikace, která má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="6e813-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e813-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e813-119">See also</span></span>

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [<span data-ttu-id="6e813-120">Zabezpečení a registr</span><span class="sxs-lookup"><span data-stu-id="6e813-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [<span data-ttu-id="6e813-121">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="6e813-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
