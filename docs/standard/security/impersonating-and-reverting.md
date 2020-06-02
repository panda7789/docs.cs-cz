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
ms.openlocfilehash: dbfd71830ace1eb8af9f55f06c9ce35c32d592bb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288014"
---
# <a name="impersonating-and-reverting"></a>Zosobnění a návrat
Někdy může být nutné získat token účtu systému Windows k zosobnění účtu systému Windows. Například vaše aplikace založená na ASP.NET může muset v různých časech jednat jménem několika uživatelů. Vaše aplikace může přijmout token, který představuje správce z Internetová informační služba (IIS), zosobnit tohoto uživatele, provést operaci a vrátit se k předchozí identitě. V dalším kroku může přijmout token ze služby IIS, který představuje uživatele s menšími právy, provede nějakou operaci a vrátí se znovu.  
  
 V situacích, kdy musí vaše aplikace zosobnit účet systému Windows, který nebyl připojen k aktuálnímu vláknu službou IIS, je nutné načíst token tohoto účtu a použít ho k aktivaci účtu. Můžete to provést provedením následujících úloh:  
  
1. Načtěte token účtu pro konkrétního uživatele voláním nespravované metody **LogonUser** . Tato metoda není v .NET Framework základní knihovny tříd, ale je umístěna v nespravované knihovně **advapi32. dll**. Přístup k metodám v nespravovaném kódu je pokročilá operace a překračuje rozsah této diskuze. Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../framework/interop/index.md). Další informace o metodě **LogonUser** a **advapi32. dll**naleznete v dokumentaci k sadě SDK platformy.  
  
2. Vytvořte novou instanci třídy **WindowsIdentity** a předejte token. Následující kód demonstruje toto volání, kde `hToken` představuje token systému Windows.  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. Zahajte zosobnění vytvořením nové instance <xref:System.Security.Principal.WindowsImpersonationContext> třídy a inicializací s <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> metodou inicializované třídy, jak je znázorněno v následujícím kódu.  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. Pokud již nepotřebujete zosobnit, zavolejte <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> metodu pro vrácení zosobnění, jak je znázorněno v následujícím kódu.  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 Pokud důvěryhodný kód již <xref:System.Security.Principal.WindowsPrincipal> k vláknu připojen objekt, můžete zavolat metodu instance **impersonate**, která nepřijímá token účtu. Všimněte si, že tato operace je užitečná pouze v případě, že objekt **WindowsPrincipal** ve vlákně představuje uživatele, který není v současné době spuštěn. Například se můžete setkat s tím, že se tato situace může vyskytnout s ověřováním systému Windows, které je zapnuté a zosobněné. V takovém případě je proces spuštěn pod účtem nakonfigurovaným ve službě Internetová informační služba (IIS), zatímco aktuální objekt zabezpečení představuje uživatele systému Windows, který přistupuje k této stránce.  
  
 Všimněte si, že ani nemůže **Zrušit** **zosobnění** ani zrušení změn objektu **zabezpečení** ( <xref:System.Security.Principal.IPrincipal> ) přidruženého k aktuálnímu kontextu volání. Místo toho jsou zosobnění a vrácení změn tokenu přidruženého k aktuálnímu procesu operačního systému.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [Objekty zabezpečení a identity](principal-and-identity-objects.md)
- [Spolupráce s nespravovaným kódem](../../framework/interop/index.md)
