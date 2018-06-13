---
title: Stažení balíčku registru pro ověřování názvů vydavatelů
ms.date: 03/30/2017
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 03b68f4b9dc6fde02c951968067e0311e4981d33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398746"
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
