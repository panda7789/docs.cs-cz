---
title: 'Postupy: Vytváření objektů GenericPrincipal a GenericIdentity'
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
ms.openlocfilehash: 10a71185db3359cda1c3bf7a12f5698929c98296
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290860"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="4772d-102">Postupy: Vytváření objektů GenericPrincipal a GenericIdentity</span><span class="sxs-lookup"><span data-stu-id="4772d-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

<span data-ttu-id="4772d-103"><xref:System.Security.Principal.GenericIdentity>Třídu můžete ve spojení s <xref:System.Security.Principal.GenericPrincipal> třídou použít k vytvoření autorizačního schématu, které existuje nezávisle na doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4772d-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="4772d-104">Vytvoření objektu GenericPrincipal</span><span class="sxs-lookup"><span data-stu-id="4772d-104">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="4772d-105">Vytvořte novou instanci třídy identity a inicializujte ji s názvem, který má být uchováván.</span><span class="sxs-lookup"><span data-stu-id="4772d-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="4772d-106">Následující kód vytvoří nový objekt **GenericIdentity** a inicializuje jej s názvem `MyUser` .</span><span class="sxs-lookup"><span data-stu-id="4772d-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="4772d-107">Vytvořte novou instanci třídy **GenericPrincipal** a inicializujte ji pomocí dříve vytvořeného objektu **GenericIdentity** a pole řetězců, které představuje role, které mají být přidruženy k tomuto objektu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4772d-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="4772d-108">Následující příklad kódu určuje pole řetězců, které reprezentují roli správce a roli uživatele.</span><span class="sxs-lookup"><span data-stu-id="4772d-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="4772d-109">**GenericPrincipal** se pak inicializuje s předchozím **GenericIdentity** a polem řetězců.</span><span class="sxs-lookup"><span data-stu-id="4772d-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="4772d-110">Použijte následující kód k připojení objektu zabezpečení k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="4772d-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="4772d-111">To je užitečné v situacích, kdy je nutné ověřit objekt zabezpečení několikrát, musí být ověřen jiným kódem spuštěným ve vaší aplikaci nebo musí být ověřen <xref:System.Security.Permissions.PrincipalPermission> objektem.</span><span class="sxs-lookup"><span data-stu-id="4772d-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="4772d-112">Můžete i nadále provádět ověřování na základě rolí u objektu zabezpečení bez jeho připojení ke vláknu.</span><span class="sxs-lookup"><span data-stu-id="4772d-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="4772d-113">Další informace naleznete v tématu [nahrazování objektu zabezpečení](replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="4772d-113">For more information, see [Replacing a Principal Object](replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="4772d-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4772d-114">Example</span></span>

<span data-ttu-id="4772d-115">Následující příklad kódu ukazuje, jak vytvořit instanci třídy **GenericPrincipal** a **GenericIdentity**.</span><span class="sxs-lookup"><span data-stu-id="4772d-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="4772d-116">Tento kód zobrazí hodnoty těchto objektů do konzoly.</span><span class="sxs-lookup"><span data-stu-id="4772d-116">This code displays the values of these objects to the console.</span></span>

```vb
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
        ' PrincipalPermission object is used.
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
    // PrincipalPermission object is used.
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

<span data-ttu-id="4772d-117">Po spuštění aplikace zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="4772d-117">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="4772d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4772d-118">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="4772d-119">Nahrazení objektu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4772d-119">Replacing a Principal Object</span></span>](replacing-a-principal-object.md)
- [<span data-ttu-id="4772d-120">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="4772d-120">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
