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
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a>Postupy: Vytváření objektů GenericPrincipal a GenericIdentity – objekty
Můžete použít <xref:System.Security.Principal.GenericIdentity> třídy ve spojení s <xref:System.Security.Principal.GenericPrincipal> třídy za účelem vytvoření schématu autorizace, které existuje nezávisle na doméně Windows.  
  
### <a name="to-create-a-genericprincipal-object"></a>K vytvoření objektů GenericPrincipal  
  
1.  Vytvořit novou instanci třídy identity a inicializujte ji s názvem, který chcete, aby uchování. Následující kód vytvoří novou **GenericIdentity** objektu a inicializuje ji s názvem `MyUser`.  
  
    ```vb  
    Dim myIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity myIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  Vytvořit novou instanci třídy **GenericPrincipal** třídy a inicializovat pomocí dříve vytvořeného **GenericIdentity** objektu a pole řetězců, které představují role, které mají přiřazené k Tento objekt zabezpečení. Následující příklad kódu určuje pole řetězců, které představují role správce a role uživatele. **GenericPrincipal** je potom inicializován s předchozím **GenericIdentity** a pole řetězců.  
  
    ```vb  
    Dim myStringArray As String() = {"Manager", "Teller"}  
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)  
    ```  
  
    ```csharp  
    String[] myStringArray = {"Manager", "Teller"};  
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);  
    ```  
  
3.  Použijte následující kód k připojení objektu zabezpečení pro aktuální vlákno. To je užitečné v situacích, kde objekt zabezpečení musí být ověřené několikrát, musí být ověřené jiných kódem spuštěným v aplikaci nebo musí být ověřené pomocí <xref:System.Security.Permissions.PrincipalPermission> objektu. Ověřování na základě role můžete stále provádět na objekt zabezpečení bez připojení k vláknu. Další informace najdete v tématu [nahrazení objektu zabezpečení](../../../docs/standard/security/replacing-a-principal-object.md).  
  
    ```vb  
    Thread.CurrentPrincipal = myPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = myPrincipal;  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit instanci **GenericPrincipal** a **GenericIdentity**. Tento kód zobrazí hodnoty těchto objektů do konzoly.  
  
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
  
 Při spuštění aplikace zobrazí výstup podobný následujícímu.  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [Nahrazení objektu zabezpečení](../../../docs/standard/security/replacing-a-principal-object.md)
- [Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)
