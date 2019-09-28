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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f768242bffe619051779f87e950138ae9fcec6c
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353184"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="3f109-102">Postupy: Vytváření objektů GenericPrincipal a GenericIdentity</span><span class="sxs-lookup"><span data-stu-id="3f109-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

<span data-ttu-id="3f109-103">Třídu <xref:System.Security.Principal.GenericIdentity> ve spojení s třídou <xref:System.Security.Principal.GenericPrincipal> můžete použít k vytvoření autorizačního schématu, které existuje nezávisle na doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3f109-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="3f109-104">Vytvoření objektu GenericPrincipal</span><span class="sxs-lookup"><span data-stu-id="3f109-104">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="3f109-105">Vytvořte novou instanci třídy identity a inicializujte ji s názvem, který má být uchováván.</span><span class="sxs-lookup"><span data-stu-id="3f109-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="3f109-106">Následující kód vytvoří nový objekt **GenericIdentity** a inicializuje jej s názvem `MyUser`.</span><span class="sxs-lookup"><span data-stu-id="3f109-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="3f109-107">Vytvořte novou instanci třídy **GenericPrincipal** a inicializujte ji pomocí dříve vytvořeného objektu **GenericIdentity** a pole řetězců, které představuje role, které mají být přidruženy k tomuto objektu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3f109-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="3f109-108">Následující příklad kódu určuje pole řetězců, které reprezentují roli správce a roli uživatele.</span><span class="sxs-lookup"><span data-stu-id="3f109-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="3f109-109">**GenericPrincipal** se pak inicializuje s předchozím **GenericIdentity** a polem řetězců.</span><span class="sxs-lookup"><span data-stu-id="3f109-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="3f109-110">Použijte následující kód k připojení objektu zabezpečení k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="3f109-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="3f109-111">To je užitečné v situacích, kdy je nutné ověřit objekt zabezpečení několikrát, musí být ověřen jiným kódem spuštěným v aplikaci nebo musí být ověřen objektem <xref:System.Security.Permissions.PrincipalPermission>.</span><span class="sxs-lookup"><span data-stu-id="3f109-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="3f109-112">Můžete i nadále provádět ověřování na základě rolí u objektu zabezpečení bez jeho připojení ke vláknu.</span><span class="sxs-lookup"><span data-stu-id="3f109-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="3f109-113">Další informace naleznete v tématu [nahrazování objektu zabezpečení](../../../docs/standard/security/replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="3f109-113">For more information, see [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="3f109-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f109-114">Example</span></span>

<span data-ttu-id="3f109-115">Následující příklad kódu ukazuje, jak vytvořit instanci třídy **GenericPrincipal** a **GenericIdentity**.</span><span class="sxs-lookup"><span data-stu-id="3f109-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="3f109-116">Tento kód zobrazí hodnoty těchto objektů do konzoly.</span><span class="sxs-lookup"><span data-stu-id="3f109-116">This code displays the values of these objects to the console.</span></span>

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

<span data-ttu-id="3f109-117">Po spuštění aplikace zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="3f109-117">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="3f109-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f109-118">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="3f109-119">Nahrazení objektu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3f109-119">Replacing a Principal Object</span></span>](../../../docs/standard/security/replacing-a-principal-object.md)
- [<span data-ttu-id="3f109-120">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="3f109-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
