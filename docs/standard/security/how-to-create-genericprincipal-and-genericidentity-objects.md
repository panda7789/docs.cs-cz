---
title: 'Postupy: Vytváření objektů GenericPrincipal a GenericIdentity'
ms.date: 07/15/2020
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
ms.openlocfilehash: 903d636938c47850951330d7936d95470441607e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557213"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a>Postupy: Vytváření objektů GenericPrincipal a GenericIdentity

> [!NOTE]
> Tento článek se týká systému Windows.
>
> Informace o ASP.NET Core najdete v tématu [Přehled zabezpečení ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/).

<xref:System.Security.Principal.GenericIdentity>Třídu můžete ve spojení s <xref:System.Security.Principal.GenericPrincipal> třídou použít k vytvoření autorizačního schématu, které existuje nezávisle na doméně systému Windows.

### <a name="to-create-a-genericprincipal-object"></a>Vytvoření objektu GenericPrincipal

1. Vytvořte novou instanci třídy identity a inicializujte ji s názvem, který má být uchováván. Následující kód vytvoří nový objekt **GenericIdentity** a inicializuje jej s názvem `MyUser` .

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. Vytvořte novou instanci třídy **GenericPrincipal** a inicializujte ji pomocí dříve vytvořeného objektu **GenericIdentity** a pole řetězců, které představuje role, které mají být přidruženy k tomuto objektu zabezpečení. Následující příklad kódu určuje pole řetězců, které reprezentují roli správce a roli uživatele. **GenericPrincipal** se pak inicializuje s předchozím **GenericIdentity** a polem řetězců.

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. Použijte následující kód k připojení objektu zabezpečení k aktuálnímu vláknu. To je užitečné v situacích, kdy je nutné ověřit objekt zabezpečení několikrát, musí být ověřen jiným kódem spuštěným ve vaší aplikaci nebo musí být ověřen <xref:System.Security.Permissions.PrincipalPermission> objektem. Můžete i nadále provádět ověřování na základě rolí u objektu zabezpečení bez jeho připojení ke vláknu. Další informace naleznete v tématu [nahrazování objektu zabezpečení](replacing-a-principal-object.md).

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak vytvořit instanci třídy **GenericPrincipal** a **GenericIdentity**. Tento kód zobrazí hodnoty těchto objektů do konzoly.

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

Po spuštění aplikace zobrazí výstup podobný následujícímu.

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a>Viz také

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [Nahrazení objektu zabezpečení](replacing-a-principal-object.md)
- [Objekty zabezpečení a identity](principal-and-identity-objects.md)
