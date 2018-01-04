---
title: "Postupy: Vytváření objektů GenericPrincipal a GenericIdentity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b10029c8b290ffaaa4a858fe3e5a6315031f1bab
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a>Postupy: Vytváření objektů GenericPrincipal a GenericIdentity
Můžete použít <xref:System.Security.Principal.GenericIdentity> třídy ve spojení s <xref:System.Security.Principal.GenericPrincipal> třídy za účelem vytvoření schématu autorizace, které existuje nezávislé domény systému Windows.  
  
### <a name="to-create-a-genericprincipal-object"></a>K vytvoření objektů GenericPrincipal  
  
1.  Vytvořit novou instanci třídy identity a provést jeho inicializaci s názvem, který chcete, aby udržení. Následující kód vytvoří novou **GenericIdentity** objektu a inicializuje s názvem `MyUser`.  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  Vytvořit novou instanci třídy **GenericPrincipal** třídy a provést jeho inicializaci s dříve vytvořenou **GenericIdentity** objekt a pole řetězců, které představují role, které chcete přidružené Tento objekt zabezpečení. Následující příklad kódu určuje pole řetězců, které představují role správce a roli uživatele. **GenericPrincipal** je potom inicializován předchozí **GenericIdentity** a v poli řetězců.  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  Použijte následující kód k připojení k objektu zabezpečení pro aktuální vlákno. To je důležité v situacích, kde objekt zabezpečení musí být ověřen několikrát, musí být ověřen jiný kód spuštěný ve vaší aplikaci nebo musí být ověřené pomocí <xref:System.Security.Permissions.PrincipalPermission> objektu. Stále je možné provést ověřování na základě rolí na objekt zabezpečení bez připojení k vlákno. Další informace najdete v tématu [nahrazení objektu zabezpečení](../../../docs/standard/security/replacing-a-principal-object.md).  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Principal.GenericIdentity>  
 <xref:System.Security.Principal.GenericPrincipal>  
 <xref:System.Security.Permissions.PrincipalPermission>  
 [Nahrazení objektu zabezpečení](../../../docs/standard/security/replacing-a-principal-object.md)  
 [Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)
