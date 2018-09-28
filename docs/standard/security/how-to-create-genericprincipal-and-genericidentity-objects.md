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
ms.openlocfilehash: 79b5e05fe9133eb2282eedefa001e64ece5e0f57
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2018
ms.locfileid: "47421135"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a>Postupy: Vytváření objektů GenericPrincipal a GenericIdentity
Můžete použít <xref:System.Security.Principal.GenericIdentity> třídy ve spojení s <xref:System.Security.Principal.GenericPrincipal> třídy za účelem vytvoření schématu autorizace, které existuje nezávisle na doméně Windows.  
  
### <a name="to-create-a-genericprincipal-object"></a>K vytvoření objektů GenericPrincipal  
  
1.  Vytvořit novou instanci třídy identity a inicializujte ji s názvem, který chcete, aby uchování. Následující kód vytvoří novou **GenericIdentity** objektu a inicializuje ji s názvem `MyUser`.  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  Vytvořit novou instanci třídy **GenericPrincipal** třídy a inicializovat pomocí dříve vytvořeného **GenericIdentity** objektu a pole řetězců, které představují role, které mají přiřazené k Tento objekt zabezpečení. Následující příklad kódu určuje pole řetězců, které představují role správce a role uživatele. **GenericPrincipal** je potom inicializován s předchozím **GenericIdentity** a pole řetězců.  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  Použijte následující kód k připojení objektu zabezpečení pro aktuální vlákno. To je užitečné v situacích, kde objekt zabezpečení musí být ověřené několikrát, musí být ověřené jiných kódem spuštěným v aplikaci nebo musí být ověřené pomocí <xref:System.Security.Permissions.PrincipalPermission> objektu. Ověřování na základě role můžete stále provádět na objekt zabezpečení bez připojení k vláknu. Další informace najdete v tématu [nahrazení objektu zabezpečení](../../../docs/standard/security/replacing-a-principal-object.md).  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
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
        Dim MyIdentity As New GenericIdentity("MyIdentity")  
  
        ' Create generic principal.  
        Dim MyStringArray As String() =  {"Manager", "Teller"}  
        Dim MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
  
        ' Attach the principal to the current thread.  
        ' This is not required unless repeated validation must occur,  
        ' other code in your application must validate, or the   
        ' PrincipalPermisson object is used.   
        Thread.CurrentPrincipal = MyPrincipal  
  
        ' Print values to the console.  
        Dim Name As String = MyPrincipal.Identity.Name  
        Dim Auth As Boolean = MyPrincipal.Identity.IsAuthenticated  
        Dim IsInRole As Boolean = MyPrincipal.IsInRole("Manager")  
  
        Console.WriteLine("The Name is: {0}", Name)  
        Console.WriteLine("The IsAuthenticated is: {0}", Auth)  
        Console.WriteLine("Is this a Manager? {0}", IsInRole)  
  
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
    GenericIdentity MyIdentity = new GenericIdentity("MyIdentity");  
  
    // Create generic principal.  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal =   
        new GenericPrincipal(MyIdentity, MyStringArray);  
  
    // Attach the principal to the current thread.  
    // This is not required unless repeated validation must occur,  
    // other code in your application must validate, or the   
    // PrincipalPermisson object is used.   
    Thread.CurrentPrincipal = MyPrincipal;  
  
    // Print values to the console.  
    String Name =  MyPrincipal.Identity.Name;  
    bool Auth =  MyPrincipal.Identity.IsAuthenticated;   
    bool IsInRole =  MyPrincipal.IsInRole("Manager");  
  
    Console.WriteLine("The Name is: {0}", Name);  
    Console.WriteLine("The IsAuthenticated is: {0}", Auth);  
    Console.WriteLine("Is this a Manager? {0}", IsInRole);  
  
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
