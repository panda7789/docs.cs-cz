---
title: Přidat odkaz webové služby WCF
description: Přehled Microsoft WCF Web Service Reference Provider nástroj, který přidá funkce pro projekty .NET Core a ASP.NET Core, podobně jako přidat odkaz na službu pro projekty .NET Framework.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 806f6e90aedc669c3a56ce1cde64311bdd4af32c
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63774283"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a>Použijte nástroj WCF Web Service odkaz na poskytovatele

V průběhu let, celá řada vývojářů sady Visual Studio pracovalo produktivity, která [ **přidat odkaz na službu** ](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) nástroje, které jsou k dispozici v případě potřeby svých projektů rozhraní .NET Framework pro přístup k webovým službám.  **WCF Web Service Reference** nástroj je rozšíření sady Visual Studio připojené služby, která poskytuje stejně jako funkce Přidat odkaz na službu pro .NET Core a ASP.NET Core projekty. Tento nástroj načte metadata z webové služby v aktuálním řešení, na umístění v síti, nebo ze souboru WSDL a vytvoří soubor kompatibilní zdroj .NET Core obsahující kód na proxy serveru klienta Windows Communication Foundation (WCF), který používáte pro přístup k webu Služba.

> [!IMPORTANT]
> Služby by měly odkazovat pouze z důvěryhodného zdroje. Přidávání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) nebo novější verze

## <a name="how-to-use-the-extension"></a>Jak používat rozšíření

> [!NOTE]
> **WCF Web Service Reference** možnost se vztahuje na projekty vytvořené pomocí následující šablony projektů:
> * **Visual C#** > **.NET Core**
> * **Visual C#** > **.NET Standard**
> * **Visual C#** > **Web** > **ASP.NET Core Web Application**

Použití **webové aplikace ASP.NET Core** šablony projektu jako příklad, tento článek vás provede přidáním odkazu na službu WCF do projektu:

1. V Průzkumníku řešení poklikejte **připojené služby** uzlu projektu (pro projekt .NET Core nebo .NET Standard tato možnost je k dispozici, když kliknete pravým tlačítkem na **závislosti** uzlu projekt v Průzkumníku řešení).

    **Připojené služby** stránka se zobrazí, jak je znázorněno na následujícím obrázku:

    ![Visual Studio Connected Services kartu pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Na **připojené služby** klikněte na **Microsoft WCF Web Service Reference Provider**. Tím se zobrazí **konfigurace WCF Web Service Reference** průvodce:

    ![Visual Studio koncový bod služby kartu pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Vyberte službu.

    3a. Nejsou k dispozici v rámci několika možností hledání služeb **konfigurace WCF Web Service Reference** průvodce:

     * K vyhledání služby definované v aktuálním řešení, klikněte na tlačítko **Discover** tlačítko.
     * K vyhledání služeb hostovaných na zadané adrese, zadejte adresu URL služby v **adresu** pole a klikněte na tlačítko **Přejít** tlačítko.
     * Pokud chcete vybrat soubor WSDL, který obsahuje informace o webových službách metadat, klikněte na tlačítko **Procházet** tlačítko.

    3b. Tuto službu vybrat ze seznamu výsledků hledání v **služby** pole. V případě potřeby zadejte obor názvů pro generovaný kód z odpovídajících **Namespace** textového pole.

    3c. Klikněte na tlačítko **Další** tlačítko Otevřít **možnosti datového typu** a **možnosti klienta** stránky. Alternativně klepněte na tlačítko **Dokončit** tlačítko a použijte výchozí možnosti.

4. **Možnosti datového typu** formuláře můžete upřesnit nastavení konfigurace odkazu generované služby:

    ![Visual Studio datový typ možnosti pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > **Znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko možnost je užitečná, když datové typy, které jsou potřeba pro generování kódu pro odkaz na službu jsou definovány v jednom z odkazovaných sestavení vašeho projektu.  Je důležité pro opětovné použití těchto existující datové typy, abyste předešli problémům s konflikt nebo modul runtime typu v době kompilace.

    Může docházet k prodlevám při načítání informací o typu, v závislosti na počtu závislostí projektu a dalších faktorů výkon systému. **Dokončit** během načítání, pokud je tlačítko neaktivní **znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko je zaškrtnuté políčko.

5. Klikněte na tlačítko **Dokončit** až budete hotovi.

Při zobrazování průběhu, nástroj:

* Soubory ke stažení metadat ze služby WCF.
* Generuje kód odkazu na službu do souboru s názvem *reference.cs*a přidá jej do projektu v rámci **připojené služby** uzlu.
* Aktualizuje soubor projektu (.csproj) s odkazy na balíčky NuGet, které vyžaduje kompilace a spuštění na cílové platformě.

![Visual Studio průběh](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Po dokončení těchto procesů, můžete vytvořit instanci typu generovaného klienta WCF a volání operací služby.

## <a name="next-steps"></a>Další kroky

### <a name="feedback--questions"></a>Zpětná vazba a otázky

Pokud máte jakékoli dotazy nebo připomínky, [otevřete problém na Githubu](https://github.com/dotnet/wcf/issues/new). Můžete také zkontrolovat všechny stávající dotazy nebo potíže [v WCF úložišti na Githubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Zpráva k vydání verze

* Odkazovat [poznámky k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) aktualizovanou verzi informace, včetně známých problémů.
