---
title: Stažení balíčku registru pro ověřování názvů vydavatelů
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 833a0722fdd27df4e488ed7fac99444c6d9b8905
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940579"
---
# <a name="download-the-validating-issuer-name-registry-package"></a>Stažení balíčku registru ověřování názvů vydavatelů

Toto téma popisuje, jak stáhnout a použít ověřování Issuer Name Registry (VINR) ve vašem projektu.

Rozšíření VINR je k dispozici jako balíček NuGet, který přidá nezbytná sestavení a odkazy na projekt. Pokud již nemáte nainstalován nástroj NuGet, přejděte na [nuget.org](https://nuget.org) k její instalaci. Historii verzí pro rozšíření můžete zobrazit návštěvou její stránky na webu NuGet: [Microsoft ověřuje registr názvu vydavatele na NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)

## <a name="use-the-package-manager-gui"></a>Pomocí GUI Správce balíčků

1. V sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení**a pak vyberte **spravovat balíčky NuGet**.

2. V **spravovat balíčky NuGet** okna, klikněte do vyhledávacího pole a zadejte `ValidatingIssuerNameRegistry` a stiskněte klávesu **Enter**.

3. V podokně výsledků klikněte **nainstalovat** tlačítko pro první výsledek.

4. Balíček se začne stahovat. Před přidáním do projektu, zobrazí se dialogové okno přijetí licence. Pokud s licenčními podmínkami souhlasíte, klikněte na tlačítko **souhlasím**.

5. Nejnovější sestavení VINR bude stažena a přidány do projektu.

## <a name="use-the-package-manager-console"></a>Použití konzole Správce balíčků

1. V sadě Visual Studio, klikněte na tlačítko **nástroje** > **Správce balíčků NuGet** > **Konzola správce balíčků**.

2. **Konzola správce balíčků** se zobrazí. Zadejte následující text a stiskněte klávesu **Enter**:

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. Nejnovější sestavení VINR bude stažena a přidány do projektu.