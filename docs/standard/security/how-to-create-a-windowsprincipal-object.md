---
title: "Postupy: Vytvoření objektu WindowsPrincipal"
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
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c4eb890696162af61f1355bfca50ce5dd2a615ad
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Postupy: Vytvoření objektu WindowsPrincipal
Existují dva způsoby, jak vytvořit <xref:System.Security.Principal.WindowsPrincipal> objektu, v závislosti na tom, zda kód musí opakovaně provádět ověřování na základě rolí nebo musí provést pouze jednou.  
  
 Pokud kód musí opakovaně provádět ověřování na základě rolí, první z následujících postupů produkuje menší režii. Pokud kód potřebuje provést ověření na základě rolí, pouze jednou, můžete vytvořit <xref:System.Security.Principal.WindowsPrincipal> objekt pomocí druhého z následujících postupů.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>K vytvoření objektu WindowsPrincipal pro opakované ověření  
  
1.  Volání <xref:System.AppDomain.SetPrincipalPolicy%2A> metodu <xref:System.AppDomain> objekt, který je vrácen statickou <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> vlastnost předávání metodu <xref:System.Security.Principal.PrincipalPolicy> hodnotu výčtu, která určuje, co by měla být nové zásady. Podporované hodnoty jsou <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, a <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. Následující kód ukazuje volání této metody.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  Se zásadami, nastavit, použijte statickou <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost načíst objekt, který zapouzdřuje aktuálního uživatele systému Windows. Vzhledem k tomu vlastnost návratový typ je <xref:System.Security.Principal.IPrincipal>, musíte vysílat výsledek, který má <xref:System.Security.Principal.WindowsPrincipal> typu. Následující kód inicializuje novou <xref:System.Security.Principal.WindowsPrincipal> objektu na hodnotu objektu zabezpečení přidružené k aktuální vlákno.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  Po vytvoření objektu zabezpečení, můžete některou z několika metod pro jeho ověření.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>K vytvoření objektu WindowsPrincipal pro jedno ověření  
  
1.  Inicializace novou <xref:System.Security.Principal.WindowsIdentity> objekt voláním statické <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> metoda, která dotazuje aktuální účet systému Windows a umístí informace o tento účet do nově vytvořené identity objektu. Následující kód vytvoří novou <xref:System.Security.Principal.WindowsIdentity> objektu a inicializuje aktuálně ověřeného uživatele.  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  Vytvořte novou <xref:System.Security.Principal.WindowsPrincipal> objektu a předejte ji hodnotu <xref:System.Security.Principal.WindowsIdentity> objekt vytvořený v předchozím kroku.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  Po vytvoření objektu zabezpečení, můžete některou z několika metod pro jeho ověření.  
  
## <a name="see-also"></a>Viz také  
 [Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)
