---
title: Přidat odkaz na webovou službu WCF
description: Přehled nástroje Microsoft WCF Web Service Reference Provider Tool, který přidává funkce pro projekty .NET Core a ASP.NET Core, podobně jako přidat odkaz na službu pro projekty rozhraní .NET Framework.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc
ms.openlocfilehash: cdd6b457d289dd7b752c97c5645f0797f24b72aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715674"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a>Použití nástroje WCF Web Service Reference Provider Tool

V průběhu let mnoho vývojářů sady Visual Studio si užilo produktivitu, kterou nástroj [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) poskytl, když jejich projekty rozhraní .NET Framework potřebovaly přístup k webovým službám.  Nástroj **WCF Web Service Reference** je rozšíření připojené služby visual studia, které poskytuje prostředí, jako je funkce Přidat odkaz na službu pro projekty .NET Core a ASP.NET Core. Tento nástroj načte metadata z webové služby v aktuálním řešení, v síťovém umístění nebo ze souboru WSDL a vygeneruje zdrojový soubor kompatibilní s rozhraním .NET Core obsahující kód proxy klienta WCF (Windows Communication Foundation), který můžete použít pro přístup k webu. Služby.

> [!IMPORTANT]
> Měli byste odkazovat pouze na služby z důvěryhodného zdroje. Přidání odkazů z nedůvěryhodného zdroje může ohrozit zabezpečení.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 verze 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) nebo novější verze

## <a name="how-to-use-the-extension"></a>Jak používat rozšíření

> [!NOTE]
> Možnost **WCF Web Service Reference** je použitelná pro projekty vytvořené pomocí následujících šablon projektu:
>
> - **Visual C#** > **.NET Core**
> - **Visual C#** > **.NET Standard**
> - **Visual C#** > **Webová** > ASP.NET základní**webová aplikace** Visual C#

Pomocí šablony projektu **ASP.NET základní webové aplikace** jako příklad vás tento článek provede přidáním odkazu na službu WCF do projektu:

1. V Průzkumníku řešení poklepejte na uzel **Připojené služby** projektu (pro projekt .NET Core nebo .NET Standard je tato možnost k dispozici po klepnutí pravým tlačítkem myši na uzel **Závislosti** projektu v Průzkumníku řešení).

    Stránka **Připojené služby** se zobrazí na následujícím obrázku:

    ![Karta Propojená služba Visual Studio pro jádro rozhraní .NET](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Na stránce **Připojené služby** klepněte na **položku Microsoft WCF Web Service Reference Provider**. Tím se zobrazí Průvodce **odkazem na konfiguraci webové služby WCF:**

    ![Karta Koncový bod služby Visual Studio pro jádro rozhraní .NET](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Vyberte službu.

    3a. V průvodci konfigurovat referenční webové **služby WCF** je k dispozici několik možností vyhledávání služeb:

     * Chcete-li vyhledat služby definované v aktuálním řešení, klepněte na tlačítko **Zjistit.**
     * Chcete-li vyhledat služby hostované na zadané adrese, zadejte adresu URL služby do pole **Adresa** a klepněte na tlačítko **Přejít.**
     * Chcete-li vybrat soubor WSDL, který obsahuje informace o metadatech webové služby, klepněte na tlačítko **Procházet.**

    3b. Vyberte službu ze seznamu výsledků hledání v poli **Služby.** V případě potřeby zadejte obor názvů pro generovaný kód do odpovídajícího textového pole **Jmenný prostor.**

    3c. Klepnutím na tlačítko **Další** otevřete **možnosti datového typu** a stránky **Možnosti klienta.** Případně můžete klepnutím na tlačítko **Dokončit** použít výchozí možnosti.

4. Formulář **Možnosti datového typu** umožňuje upřesnit nastavení konfigurace odkazu na vygenerovanou službu:

    ![Karta Možnosti datového typu sady Visual Studio pro jádro rozhraní .NET](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > Možnost **Znovu použít typy v odkazovaných sestaveních** je užitečná, když jsou datové typy potřebné pro generování referenčního kódu služby definovány v jednom z odkazovaných sestavení projektu.  Je důležité znovu použít tyto existující datové typy, aby se zabránilo sopakování typu kompilace nebo problémům za běhu.

    Může dojít ke zpoždění při načítání informací o typu, v závislosti na počtu závislostí projektu a dalších faktorech výkonu systému. Tlačítko **Dokončit** je během načítání zakázáno, pokud není zaškrtnuto políčko **Znovu použít v odkazovaných sestavách.**

5. Po dokončení klepněte na **tlačítko Dokončit.**

Při zobrazování průběhu nástroj:

- Stáhne metadata ze služby WCF.
- Generuje referenční kód služby v souboru s názvem *reference.cs*a přidá jej do projektu v uzlu **Připojené služby.**
- Aktualizuje soubor projektu (.csproj) s Odkazy na balíček NuGet potřebné ke kompilaci a spuštění na cílové platformě.

![Okno Průběh sady Visual Studio](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Po dokončení těchto procesů můžete vytvořit instanci generovaného typu klienta WCF a vyvolat operace služby.

## <a name="see-also"></a>Viz také

- [Začínáme s aplikacemi Windows Communication Foundation](../../framework/wcf/getting-started-tutorial.md)
- [Služby Windows Communication Foundation a datové služby WCF v sadě Visual Studio](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [Funkce podporované wcf na .NET Core](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a>Zpětná vazba & otázky

Máte-li jakékoli dotazy nebo zpětnou vazbu, nahlaste to v [komunitě vývojářů](https://developercommunity.visualstudio.com/) pomocí nástroje [Nahlásit problém.](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)

## <a name="release-notes"></a>Poznámky k verzi

- Aktualizované informace o verzi, včetně známých problémů, naleznete v [poznámkách k verzi.](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md)
