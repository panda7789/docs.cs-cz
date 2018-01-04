---
title: "Zosobnění a návrat"
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
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 869b9aadfa236a39d9807062e61046922e382d13
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="impersonating-and-reverting"></a>Zosobnění a návrat
V některých případech budete muset získat token účtu Windows zosobnit účet systému Windows. Například aplikace založený na technologii ASP.NET může mít zastupovat několika uživatelům v různých časech. Aplikace může přijmout token, který představuje správce z Internetové informační služby (IIS), zosobnit uživatele, provedení určité operace a vrátit k předchozí identitu. V dalším kroku ji může přijmout token ze služby IIS, který reprezentuje uživatele s menším počtem práv, provádět některé operace a vracet znovu.  
  
 V situacích, kde vaše aplikace musí zosobnit účet Windows, který nebyl přidán do aktuální vlákno službou IIS je nutné získat token tohoto účtu a použít ho k aktivaci účtu. To provedete tak, že provedete následující úlohy:  
  
1.  Získat token účtu pro určitého uživatele tím, že zavoláte na nespravovanou **LogonUser** metoda. Tato metoda není v knihovně základní třídy rozhraní .NET Framework, ale je umístěn v nespravovanou **advapi32.dll**. Přístup k metodám v nespravovaném kódu je pokročilá operace a je nad rámec této diskuse. Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md). Další informace o **LogonUser** metoda a **advapi32.dll**, naleznete v dokumentaci k sadě SDK pro platformu.  
  
2.  Vytvořit novou instanci třídy **WindowsIdentity** třídy a předejte token. Následující kód ukazuje toto volání, kde `hToken` představuje tokenu systému Windows.  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  Nejprve vytvořit novou instanci třídy zosobnění <xref:System.Security.Principal.WindowsImpersonationContext> třídy a inicializací s <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> metoda inicializované třídy, jak je znázorněno v následujícím kódu.  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  Pokud již nepotřebujete zosobnění, volejte <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> metoda k uloženému zosobnění, jak je znázorněno v následujícím kódu.  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 Pokud důvěryhodný kód již připojil <xref:System.Security.Principal.WindowsPrincipal> objektu vlákna, můžete volat metodu instance **zosobnit**, které nevyužívá token účtu. Všimněte si, že to je užitečné pouze když **WindowsPrincipal** objekt ve vlákně představuje uživatele, než ve kterém je aktuálně spuštěn proces. Například může dojít k této situaci ASP.NET pomocí ověřování systému Windows zapnuté a zosobnění vypnutý. V takovém případě je proces spuštěný pod účtem, nakonfigurovat v Internetové informační služby (IIS), pokud je aktuální objekt zabezpečení představuje uživatele systému Windows, který je přistoupit ke stránce.  
  
 Všimněte si, že ani **zosobnit** ani **vrátit zpět** změny **hlavní** objektu (<xref:System.Security.Principal.IPrincipal>) přidružené k aktuální kontext volání. Místo toho zosobnění a navrácení změnu token přidružené k aktuální proces operačního systému...  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.Security.Principal.WindowsImpersonationContext>  
 [Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)  
 [Spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md)
