---
title: 'Postupy: Vytvoření objektu WindowsPrincipal'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 016f19c7141ebaf9b5c1f03adc263b689489119b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874206"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Postupy: Vytvoření objektu WindowsPrincipal
Existují dva způsoby, jak vytvořit <xref:System.Security.Principal.WindowsPrincipal> objekt, v závislosti na tom, zda kód nutné opakovaně provádět ověřování na základě rolí nebo musí provést pouze jednou.  
  
 Pokud kód musí opakovaně provádět ověřování na základě rolí, první z těchto postupů vytváří menší nároky. Pokud kód potřebuje provést ověření na základě rolí pouze jednou, můžete vytvořit <xref:System.Security.Principal.WindowsPrincipal> s použitím sekundu z následujících postupů.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>K vytvoření objektu WindowsPrincipal pro opakované ověření  
  
1.  Volání <xref:System.AppDomain.SetPrincipalPolicy%2A> metodu na <xref:System.AppDomain> objekt, který je vrácený statické <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> vlastnost předávání metodu <xref:System.Security.Principal.PrincipalPolicy> hodnotu výčtu, která určuje, co by měl být nové zásady. Podporované hodnoty jsou <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, a <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. Následující kód ukazuje volání této metody.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  Nastavit zásady, použijte statické <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost pro načtení instanční objekt, který zapouzdřuje aktuálního uživatele Windows. Vzhledem k tomu, že vlastnost návratový typ <xref:System.Security.Principal.IPrincipal>, musíte přetypovat výsledek, který má <xref:System.Security.Principal.WindowsPrincipal> typu. Následující kód inicializuje novou <xref:System.Security.Principal.WindowsPrincipal> objektu na hodnotu objektu spojené s aktuálním vláknem.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  Po vytvoření objektu zabezpečení, můžete použít některou z několika metod abyste ověřili, že.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>K vytvoření objektu WindowsPrincipal pro jedno ověření  
  
1.  Inicializovat nový <xref:System.Security.Principal.WindowsIdentity> objektu voláním statické <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> metodu, která vyhledá aktuální účet Windows a uvádí informace o tento účet do nově vytvořeného identity objektu. Následující kód vytvoří novou <xref:System.Security.Principal.WindowsIdentity> objektu a inicializuje ji aktuálně ověřeného uživatele.  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  Vytvořte nový <xref:System.Security.Principal.WindowsPrincipal> objektu a předejte jí hodnotu <xref:System.Security.Principal.WindowsIdentity> objekt vytvořený v předchozím kroku.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  Po vytvoření objektu zabezpečení, můžete použít některou z několika metod abyste ověřili, že.  
  
## <a name="see-also"></a>Viz také:

- [Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)
