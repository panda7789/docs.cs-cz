---
title: "Stažení balíčku registru pro ověřování názvů vydavatelů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bf6869de939ed7eda7cd3de868e712126f71751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-the-validating-issuer-name-registry-package"></a>Stažení balíčku registru pro ověřování názvů vydavatelů
Toto téma popisuje, jak stáhnout a použít registru název vystavitele (VINR) ověřování ve vašem projektu.  
  
## <a name="downloading-the-validating-issuer-name-registry"></a>Stahování ověřování registru název vystavitele  
 VINR je k dispozici jako balíčku NuGet, který přidá nezbytné sestavení a odkazy na projekt. Pokud již nemáte NuGet nainstalovaná, přejděte na [nuget.org](http://nuget.org) k její instalaci. Zobrazí historii Správa verzí pro rozšíření navštivte stránku s jeho na NuGet: [Microsoft ověřování vystavitele název registru na NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a>Stahování registru název vystavitele ověřování pomocí grafického uživatelského rozhraní Správce balíčků  
  
1.  V sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníku řešení**a potom vyberte **spravovat balíčky NuGet**.  
  
2.  V **spravovat balíčky NuGet** okně klikněte na vyhledávací pole a zadejte `ValidatingIssuerNameRegistry` a stiskněte klávesu **Enter**.  
  
3.  V podokně výsledků klikněte na **nainstalovat** tlačítko pro první výsledek.  
  
4.  Balíček zahájíte stahování. Před přidáním do projektu, zobrazí se dialogové okno přijetí licence. Pokud souhlasíte s licenčními podmínkami, klikněte na tlačítko **souhlasím**.  
  
5.  Nejnovější sestavení VINR bude možné stáhnout a přidat do projektu.  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a>Stahování registru název vystavitele ověřování pomocí konzoly Správce balíčků  
  
1.  V sadě Visual Studio, klikněte na tlačítko **nástroje**, **Správce balíčků knihoven**a potom **Konzola správce balíčků**.  
  
2.  **Konzola správce balíčků** se zobrazí. Zadejte následující text a stiskněte klávesu **Enter**:  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  Nejnovější sestavení VINR bude možné stáhnout a přidat do projektu.
