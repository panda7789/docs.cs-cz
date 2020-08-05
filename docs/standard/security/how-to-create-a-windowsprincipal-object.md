---
title: 'Postupy: Vytvoření objektu WindowsPrincipal'
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET], creating a WindowsPrincipal object
- security [.NET], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: d99d63dc766f37e7cc30888d2e77657595f909af
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557031"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Postupy: Vytvoření objektu WindowsPrincipal

> [!NOTE]
> Tento článek se týká systému Windows.
>
> Informace o ASP.NET Core najdete v tématu [ASP.NET Core Security](/aspnet/core/security/).

Existují dva způsoby, jak vytvořit <xref:System.Security.Principal.WindowsPrincipal> objekt, v závislosti na tom, zda kód musí opakovaně provádět ověřování na základě rolí, nebo musí být proveden pouze jednou.  
  
Pokud kód musí opakovaně provádět ověřování na základě rolí, pak první z následujících postupů vytvoří méně režijních nákladů. Pokud kód potřebuje provést ověřování na základě role pouze jednou, můžete vytvořit <xref:System.Security.Principal.WindowsPrincipal> objekt pomocí druhého z následujících postupů.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Vytvoření objektu WindowsPrincipal pro opakované ověření  
  
1. Zavolejte <xref:System.AppDomain.SetPrincipalPolicy%2A> metodu u <xref:System.AppDomain> objektu, který je vrácený statickou <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> vlastností, předáním metody <xref:System.Security.Principal.PrincipalPolicy> hodnotu výčtu, která indikuje, co by mělo být nové zásady. Podporované hodnoty jsou <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal> , <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> a <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal> . Následující kód demonstruje toto volání metody.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. Pomocí sady zásad použijte statickou <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost k načtení objektu zabezpečení, který zapouzdřuje aktuálního uživatele systému Windows. Vzhledem k tomu, že návratový typ vlastnosti je <xref:System.Security.Principal.IPrincipal> , musíte přetypovat výsledek na <xref:System.Security.Principal.WindowsPrincipal> typ. Následující kód inicializuje nový <xref:System.Security.Principal.WindowsPrincipal> objekt na hodnotu objektu zabezpečení přidruženého k aktuálnímu vláknu.  
  
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
  
1. Inicializujte nový <xref:System.Security.Principal.WindowsIdentity> objekt voláním statické <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> metody, která se dotazuje na aktuální účet systému Windows a umístí informace o tomto účtu do nově vytvořeného objektu identity. Následující kód vytvoří nový <xref:System.Security.Principal.WindowsIdentity> objekt a inicializuje jej na aktuálně ověřeného uživatele.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. Vytvořte nový <xref:System.Security.Principal.WindowsPrincipal> objekt a předejte mu hodnotu <xref:System.Security.Principal.WindowsIdentity> objektu vytvořeného v předchozím kroku.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. Po vytvoření objektu zabezpečení můžete použít některou z několika metod k jeho ověření.  
  
## <a name="see-also"></a>Viz také

- [Objekty zabezpečení a identity](principal-and-identity-objects.md)
- [ASP.NET Core zabezpečení](https://docs.microsoft.com/aspnet/core/security/)
