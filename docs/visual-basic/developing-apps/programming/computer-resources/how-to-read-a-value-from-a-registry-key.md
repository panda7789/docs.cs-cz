---
title: 'Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: bc71dd2e3a78454236b2f6f30c2d51aa596e5b8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013982"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="771be-102">Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="771be-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>
<span data-ttu-id="771be-103">`GetValue` Metodu `My.Computer.Registry` objekt lze použít ke čtení hodnoty registru Windows.</span><span class="sxs-lookup"><span data-stu-id="771be-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="771be-104">Pokud není k dispozici klíč "Software\MyApp" v následujícím příkladu, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="771be-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="771be-105">Pokud `ValueName`, "Název" v následujícím příkladu, neexistuje, `Nothing` je vrácena.</span><span class="sxs-lookup"><span data-stu-id="771be-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="771be-106">`GetValue` Metoda slouží také k určení, zda daná hodnota existuje v klíči registru.</span><span class="sxs-lookup"><span data-stu-id="771be-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="771be-107">Když kód čte registru z webové aplikace, je aktuální uživatel je vzhledem k ověřování a zosobnění, která je implementována ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="771be-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="771be-108">K načtení hodnoty z klíče registru</span><span class="sxs-lookup"><span data-stu-id="771be-108">To read a value from a registry key</span></span>  
  
- <span data-ttu-id="771be-109">Použít `GetValue` metoda zadáním cesty a názvu) k načtení hodnoty z klíče registru.</span><span class="sxs-lookup"><span data-stu-id="771be-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="771be-110">Následující příklad přečte hodnotu `Name` z `HKEY_CURRENT_USER\Software\MyApp` a zobrazí jej v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="771be-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 <span data-ttu-id="771be-111">Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="771be-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="771be-112">V dialogu pro výběr fragmentu kódu je umístěn v **operačního systému Windows > registru**.</span><span class="sxs-lookup"><span data-stu-id="771be-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="771be-113">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="771be-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="771be-114">Chcete-li zjistit, zda je hodnota v klíči registru existuje</span><span class="sxs-lookup"><span data-stu-id="771be-114">To determine whether a value exists in a registry key</span></span>  
  
- <span data-ttu-id="771be-115">Použití `GetValue` metody k načtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="771be-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="771be-116">Následující kód ověří, zda hodnota existuje a vrátí zprávu, pokud tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="771be-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="771be-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="771be-117">Robust Programming</span></span>  
 <span data-ttu-id="771be-118">Registr obsahuje nejvyšší úrovně a kořenové klíče, které se používají k ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="771be-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="771be-119">Například HKEY_LOCAL_MACHINE kořenový klíč se používá pro ukládání nastavení na úrovni počítače používané všichni uživatelé, i když HKEY_CURRENT_USER slouží k ukládání dat specifických pro jednotlivé uživatele.</span><span class="sxs-lookup"><span data-stu-id="771be-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="771be-120">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="771be-120">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="771be-121">Název klíče je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="771be-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="771be-122">Uživatel nemá oprávnění ke čtení z klíče registru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="771be-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="771be-123">Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="771be-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="771be-124">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="771be-124">.NET Framework Security</span></span>  
 <span data-ttu-id="771be-125">Pokud chcete spustit tento proces, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.RegistryPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="771be-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="771be-126">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku, protože nedostatečná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="771be-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="771be-127">Podobně uživatel musí mít správné seznamy ACL pro vytvoření nebo zápis do nastavení.</span><span class="sxs-lookup"><span data-stu-id="771be-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="771be-128">Místní aplikace, který má oprávnění zabezpečení přístupu kódu například nemusí mít oprávnění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="771be-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="771be-129">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="771be-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="771be-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="771be-130">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [<span data-ttu-id="771be-131">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="771be-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
