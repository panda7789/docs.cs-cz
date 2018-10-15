---
title: Stažení balíčku obslužné rutiny webových tokenů JSON
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: 8f878d23afd76488de7da03f16f72cbfa43c17d7
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316477"
---
# <a name="download-the-json-web-token-handler-package"></a>Stažení balíčku obslužné rutiny tokenu JSON Web

Toto téma popisuje, jak stáhnout a použít JSON Web Token Handler ve vašem projektu.

Rozšíření obslužné rutiny webového tokenu JSON je k dispozici jako balíček NuGet, který přidá nezbytná sestavení a odkazy na projekt. Pokud již nemáte nainstalován nástroj NuGet, přejděte na [nuget.org](https://nuget.org) k její instalaci. Historii verzí pro rozšíření můžete zobrazit návštěvou její stránky na webu NuGet: [JSON Web Token Handler na Nugetu](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)

## <a name="use-the-package-manager-gui"></a>Pomocí GUI Správce balíčků

1. V sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení**a pak vyberte **spravovat balíčky NuGet**.

2. V **spravovat balíčky NuGet** okna, klikněte do vyhledávacího pole a zadejte `JWT Token Handler` a stiskněte klávesu **Enter**.

3. V podokně výsledků klikněte **nainstalovat** tlačítko pro první výsledek.

4. Balíček se začne stahovat. Před přidáním do projektu, zobrazí se dialogové okno přijetí licence. Pokud s licenčními podmínkami souhlasíte, klikněte na tlačítko **souhlasím**.

5. Nejnovější sestavení obslužné rutiny webového tokenu JSON bude stažena a přidány do projektu.

## <a name="use-the-package-manager-console"></a>Použití konzole Správce balíčků

1. V sadě Visual Studio, klikněte na tlačítko **nástroje** > **Správce balíčků NuGet** > **Konzola správce balíčků**.

2. **Konzola správce balíčků** se zobrazí. Zadejte následující text a stiskněte klávesu **Enter**:

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. Nejnovější sestavení obslužné rutiny webového tokenu JSON bude stažena a přidány do projektu.