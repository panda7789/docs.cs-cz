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
ms.openlocfilehash: 30af18b7d7b86621586c7da66eda1b37356d5565
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159777"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Postupy: Vytvoření objektu WindowsPrincipal
Existují dva způsoby, jak vytvořit objekt <xref:System.Security.Principal.WindowsPrincipal>, v závislosti na tom, zda kód musí opakovaně provádět ověřování na základě rolí, nebo musí být proveden pouze jednou.  
  
 Pokud kód musí opakovaně provádět ověřování na základě rolí, pak první z následujících postupů vytvoří méně režijních nákladů. Pokud kód musí učinit ověřování na základě role pouze jednou, můžete vytvořit objekt <xref:System.Security.Principal.WindowsPrincipal> pomocí druhého z následujících postupů.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Vytvoření objektu WindowsPrincipal pro opakované ověření  
  
1. Zavolejte metodu <xref:System.AppDomain.SetPrincipalPolicy%2A> u objektu <xref:System.AppDomain>, který je vrácený vlastností static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType>, předáním metody <xref:System.Security.Principal.PrincipalPolicy> hodnotu výčtu, která indikuje, co by mělo být nové zásady. Podporované hodnoty jsou <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>a <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. Následující kód demonstruje toto volání metody.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. Pomocí sady zásad použijte vlastnost statického <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> k načtení objektu zabezpečení, který zapouzdřuje aktuálního uživatele systému Windows. Vzhledem k tomu, že návratový typ vlastnosti je <xref:System.Security.Principal.IPrincipal>, musíte přetypovat výsledek na typ <xref:System.Security.Principal.WindowsPrincipal>. Následující kód inicializuje nový objekt <xref:System.Security.Principal.WindowsPrincipal> k hodnotě objektu zabezpečení přidruženého k aktuálnímu vláknu.  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. Po vytvoření objektu zabezpečení můžete použít některou z několika metod k jeho ověření.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>Vytvoření objektu WindowsPrincipal pro jedno ověření  
  
1. Inicializujte nový objekt <xref:System.Security.Principal.WindowsIdentity> voláním statické metody <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType>, která se dotazuje na aktuální účet systému Windows a umístí informace o tomto účtu do nově vytvořeného objektu identity. Následující kód vytvoří nový objekt <xref:System.Security.Principal.WindowsIdentity> a inicializuje jej na aktuálně ověřeného uživatele.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. Vytvořte nový objekt <xref:System.Security.Principal.WindowsPrincipal> a předejte mu hodnotu objektu <xref:System.Security.Principal.WindowsIdentity> vytvořeného v předchozím kroku.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. Po vytvoření objektu zabezpečení můžete použít některou z několika metod k jeho ověření.  
  
## <a name="see-also"></a>Viz také

- [Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)
