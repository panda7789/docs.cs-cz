---
title: 'Postupy: Vytváření objektů GenericPrincipal a GenericIdentity – objekty'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d8dd255aafe16cf0cb893ff4157b3590b3fc8d03
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583677"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="8a56e-102">Postupy: Vytváření objektů GenericPrincipal a GenericIdentity – objekty</span><span class="sxs-lookup"><span data-stu-id="8a56e-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>
<span data-ttu-id="8a56e-103">Můžete použít <xref:System.Security.Principal.GenericIdentity> třídy ve spojení s <xref:System.Security.Principal.GenericPrincipal> třídy za účelem vytvoření schématu autorizace, které existuje nezávisle na doméně Windows.</span><span class="sxs-lookup"><span data-stu-id="8a56e-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>  
  
### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="8a56e-104">K vytvoření objektů GenericPrincipal</span><span class="sxs-lookup"><span data-stu-id="8a56e-104">To create a GenericPrincipal object</span></span>  
  
1.  <span data-ttu-id="8a56e-105">Vytvořit novou instanci třídy identity a inicializujte ji s názvem, který chcete, aby uchování.</span><span class="sxs-lookup"><span data-stu-id="8a56e-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="8a56e-106">Následující kód vytvoří novou **GenericIdentity** objektu a inicializuje ji s názvem `MyUser`.</span><span class="sxs-lookup"><span data-stu-id="8a56e-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>  
  
    ```vb  
    Dim myIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity myIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  <span data-ttu-id="8a56e-107">Vytvořit novou instanci třídy **GenericPrincipal** třídy a inicializovat pomocí dříve vytvořeného **GenericIdentity** objektu a pole řetězců, které představují role, které mají přiřazené k Tento objekt zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8a56e-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="8a56e-108">Následující příklad kódu určuje pole řetězců, které představují role správce a role uživatele.</span><span class="sxs-lookup"><span data-stu-id="8a56e-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="8a56e-109">**GenericPrincipal** je potom inicializován s předchozím **GenericIdentity** a pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="8a56e-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>  
  
    ```vb  
    Dim myStringArray As String() = {"Manager", "Teller"}  
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)  
    ```  
  
    ```csharp  
    String[] myStringArray = {"Manager", "Teller"};  
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);  
    ```  
  
3.  <span data-ttu-id="8a56e-110">Použijte následující kód k připojení objektu zabezpečení pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="8a56e-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="8a56e-111">To je užitečné v situacích, kde objekt zabezpečení musí být ověřené několikrát, musí být ověřené jiných kódem spuštěným v aplikaci nebo musí být ověřené pomocí <xref:System.Security.Permissions.PrincipalPermission> objektu.</span><span class="sxs-lookup"><span data-stu-id="8a56e-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="8a56e-112">Ověřování na základě role můžete stále provádět na objekt zabezpečení bez připojení k vláknu.</span><span class="sxs-lookup"><span data-stu-id="8a56e-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="8a56e-113">Další informace najdete v tématu [nahrazení objektu zabezpečení](../../../docs/standard/security/replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="8a56e-113">For more information, see [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md).</span></span>  
  
    ```vb  
    Thread.CurrentPrincipal = myPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = myPrincipal;  
    ```  
  
## <a name="example"></a><span data-ttu-id="8a56e-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a56e-114">Example</span></span>  
 <span data-ttu-id="8a56e-115">Následující příklad kódu ukazuje, jak vytvořit instanci **GenericPrincipal** a **GenericIdentity**.</span><span class="sxs-lookup"><span data-stu-id="8a56e-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="8a56e-116">Tento kód zobrazí hodnoty těchto objektů do konzoly.</span><span class="sxs-lookup"><span data-stu-id="8a56e-116">This code displays the values of these objects to the console.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Principal  
Imports System.Threading  
  
Public Class Class1  
  
    Public Shared Sub Main()  
        ' Create generic identity.  
        Dim myIdentity As New GenericIdentity("MyIdentity")  
  
        ' Create generic principal.  
        Dim myStringArray As String() =  {"Manager", "Teller"}  
        Dim myPrincipal As New GenericPrincipal(myIdentity, myStringArray)  
  
        ' Attach the principal to the current thread.  
        ' This is not required unless repeated validation must occur,  
        ' other code in your application must validate, or the   
        ' PrincipalPermisson object is used.   
        Thread.CurrentPrincipal = myPrincipal  
  
        ' Print values to the console.  
        Dim name As String = myPrincipal.Identity.Name  
        Dim auth As Boolean = myPrincipal.Identity.IsAuthenticated  
        Dim isInRole As Boolean = myPrincipal.IsInRole("Manager")  
  
        Console.WriteLine("The name is: {0}", name)  
        Console.WriteLine("The isAuthenticated is: {0}", auth)  
        Console.WriteLine("Is this a Manager? {0}", isInRole)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Security.Principal;  
using System.Threading;  
  
public class Class1  
{  
    public static int Main(string[] args)  
    {  
    // Create generic identity.  
    GenericIdentity myIdentity = new GenericIdentity("MyIdentity");  
  
    // Create generic principal.  
    String[] myStringArray = {"Manager", "Teller"};  
    GenericPrincipal myPrincipal =   
        new GenericPrincipal(myIdentity, myStringArray);  
  
    // Attach the principal to the current thread.  
    // This is not required unless repeated validation must occur,  
    // other code in your application must validate, or the   
    // PrincipalPermisson object is used.   
    Thread.CurrentPrincipal = myPrincipal;  
  
    // Print values to the console.  
    String name =  myPrincipal.Identity.Name;  
    bool auth =  myPrincipal.Identity.IsAuthenticated;   
    bool isInRole =  myPrincipal.IsInRole("Manager");  
  
    Console.WriteLine("The name is: {0}", name);  
    Console.WriteLine("The isAuthenticated is: {0}", auth);  
    Console.WriteLine("Is this a Manager? {0}", isInRole);  
  
    return 0;  
    }  
}  
```  
  
 <span data-ttu-id="8a56e-117">Při spuštění aplikace zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="8a56e-117">When executed, the application displays output similar to the following.</span></span>  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a56e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a56e-118">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="8a56e-119">Nahrazení objektu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8a56e-119">Replacing a Principal Object</span></span>](../../../docs/standard/security/replacing-a-principal-object.md)
- [<span data-ttu-id="8a56e-120">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="8a56e-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
