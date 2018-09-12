---
title: Zosobnění a návrat
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3bc5b4a9bef51ac1591bdeb21651cee624d552b2
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514452"
---
# <a name="impersonating-and-reverting"></a>Zosobnění a návrat
Někdy můžete potřebovat k získání tokenu účtu Windows zosobnit účet Windows. Aplikace založená na technologii ASP.NET například může mít jednat jménem několika uživatelů v různých časech. Vaše aplikace může přijmout token, který představuje správce z Internetové informační služby (IIS), zosobnit uživatele, provedení určité operace a vrátit k předchozí identitu. V dalším kroku ji může přijmout token ze služby IIS, který reprezentuje uživatele s menším počtem práv, provádět některé operace a znovu vrátit.  
  
 V situacích, kdy vaše aplikace musí zosobnit účet Windows, která nebyla připojena k aktuálnímu vláknu službou IIS je nutné získat token tohoto účtu a použít ho k aktivaci účtu. Uděláte to tak provádění těchto úkolů:  
  
1.  Získat token účtu pro určitého uživatele tím, že zavoláte na nespravovanou **LogonUser** metody. Tato metoda není v knihovně základních tříd rozhraní .NET Framework, ale je umístěn v nespravovanou **advapi32.dll**. Přístup k metodám v nespravovaném kódu je pokročilá operace a je nad rámec této diskuse. Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md). Další informace o **LogonUser** metoda a **advapi32.dll**, naleznete v dokumentaci Platform SDK.  
  
2.  Vytvořit novou instanci třídy **WindowsIdentity** třídy, prochází token. Následující kód ukazuje toto volání, kde `hToken` představuje Windows token.  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  Začněte tím, že vytvoříte novou instanci třídy zosobnění <xref:System.Security.Principal.WindowsImpersonationContext> třídy a inicializuje ji <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> metoda inicializovaného třídy, jak je znázorněno v následujícím kódu.  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  Pokud už nepotřebujete k zosobnění, zavolejte <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> metoda Obnova zosobnění, jak je znázorněno v následujícím kódu.  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 Pokud je důvěryhodné, kód se už připojilo <xref:System.Security.Principal.WindowsPrincipal> objekt vlákna, můžete volat metodu instance **zosobnit**, které nepřijímá token účtu. Všimněte si, že se jedná pouze užitečné, když **WindowsPrincipal** objektu ve vlákně představuje uživatele, než pod kterým proces aktuálně spouští. Například může dojít k této situaci pomocí technologie ASP.NET s ověřováním Windows zapnutý a zosobnění vypnuté. V takovém případě je proces spuštěn pod účtem nakonfigurovat v Internetové informační služby (IIS), pokud je aktuální objekt zabezpečení představuje uživatele Windows, který je přistoupit ke stránce.  
  
 Všimněte si, že ani jeden **zosobnit** ani **zpět** změny **hlavní** objektu (<xref:System.Security.Principal.IPrincipal>) přidružené k aktuálnímu kontextu volání. Místo toho zosobnění a vracení změn token spojený s aktuální proces operačního systému...  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Principal.WindowsIdentity>  
- <xref:System.Security.Principal.WindowsImpersonationContext>  
- [Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)  
- [Spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md)
