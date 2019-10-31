---
title: Přidat odkaz na webovou službu WCF
description: Přehled nástroje Microsoft WCF Web Service Reference Provider, který přidává funkce pro projekty .NET Core a ASP.NET Core, podobně jako Přidat odkaz na službu pro .NET Framework projekty.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: feecf374e1af48f349495c13ea91b810c6b0a1c3
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191907"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a>Použití nástroje poskytovatele referencí webové služby WCF

V průběhu let mnoho vývojářů sady Visual Studio využilo produktivitu, kterou poskytuje nástroj [**Přidat odkaz na službu**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) , když jejich .NET Framework projekty potřebují pro přístup k webovým službám.  **Referenční nástroj webové služby WCF** je rozšíření propojené služby sady Visual Studio, které poskytuje prostředí, jako je funkce Přidat odkaz na službu pro projekty .NET Core a ASP.NET Core. Tento nástroj načte metadata z webové služby v aktuálním řešení, v síťovém umístění nebo ze souboru WSDL a vygeneruje Windows Communication Foundation zdrojový proxy kód kompatibilní s .NET Core, který můžete použít pro přístup k webu. službám.

> [!IMPORTANT]
> Měli byste odkazovat jenom na služby z důvěryhodného zdroje. Přidání odkazů z nedůvěryhodného zdroje může ohrozit zabezpečení.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 verze 15,5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) nebo novější verze

## <a name="how-to-use-the-extension"></a>Jak používat rozšíření

> [!NOTE]
> Možnost **odkazu webové služby WCF** je platná pro projekty vytvořené pomocí následujících šablon projektu:
>
> - **Visual C#**   >  **.NET Core**
> - **Vizuální C#**   >  **.NET Standard**
> - Webová aplikace  **C# Visual**  > **Web**  > **ASP.NET Core**

Pomocí šablony projektu **ASP.NET Core webové aplikace** jako příklad vás tento článek provede přidáním odkazu na službu WCF do projektu:

1. V Průzkumník řešení dvakrát klikněte na uzel **připojené služby** projektu (pro projekt .NET Core nebo .NET Standard je tato možnost k dispozici, když kliknete pravým tlačítkem myši na uzel **závislosti** projektu v Průzkumník řešení).

    Stránka **připojené služby** se zobrazí, jak je znázorněno na následujícím obrázku:

    ![Karta připojené služby sady Visual Studio pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Na stránce **připojené služby** klikněte na **Microsoft WCF Web Service reference Provider**. Tím se zobrazí průvodce **konfigurací odkazu na webovou službu WCF** :

    ![Karta koncového bodu služby sady Visual Studio pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Vyberte službu.

    čl. V průvodci **konfigurací odkazu webové služby WCF** je dostupných několik možností hledání služeb:

     * Pokud chcete vyhledat služby definované v aktuálním řešení, klikněte na tlačítko **Vyhledat** .
     * Pokud chcete vyhledat služby hostované na zadané adrese, zadejte adresu URL služby do pole **adresa** a klikněte na tlačítko **Přejít** .
     * Chcete-li vybrat soubor WSDL, který obsahuje informace metadat webové služby, klikněte na tlačítko **Procházet** .

    3b. Vyberte službu ze seznamu výsledků hledání v poli **služby** . V případě potřeby zadejte obor názvů pro vygenerovaný kód do textového pole odpovídající **obor názvů** .

    3C. Kliknutím na tlačítko **Další** otevřete **Možnosti datový typ** a stránky **Možnosti klienta** . Případně můžete kliknutím na tlačítko **Dokončit** použít výchozí možnosti.

4. Formulář **Možnosti datového typu** umožňuje upřesnit vygenerovaná nastavení konfigurace odkazu na službu:

    ![Karta možnosti datového typu sady Visual Studio pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > Možnost **znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko je užitečná, pokud jsou datové typy potřebné pro generování kódu odkazu na službu definovány v jednom z odkazovaných sestavení projektu.  Je důležité znovu použít tyto existující datové typy, aby nedocházelo ke konfliktům typu v době kompilace nebo běhovým problémům.

    Může dojít ke zpoždění, pokud jsou načteny informace o typu, v závislosti na počtu závislostí projektu a dalších systémových faktorech výkonu. Tlačítko **Dokončit** je během načítání zakázáno, pokud není zaškrtnuté políčko **znovu použít typy v odkazovaných sestaveních** .

5. Po dokončení klikněte na **Dokončit** .

Během zobrazování průběhu nástroje:

- Stáhne metadata ze služby WCF.
- Generuje kód odkazu na službu v souboru s názvem *reference.cs*a přidá ho do projektu pod uzlem **připojené služby** .
- Aktualizuje soubor projektu (. csproj) pomocí odkazů na balíček NuGet potřebných pro zkompilování a spuštění na cílové platformě.

![Okno průběhu sady Visual Studio](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Po dokončení těchto procesů můžete vytvořit instanci vygenerovaného typu klienta WCF a vyvolat operace služby.

## <a name="see-also"></a>Viz také:

- [Začínáme s Windows Communication Foundation aplikacemi](../../framework/wcf/getting-started-tutorial.md)
- [Služby Windows Communication Foundation Services a WCF Data Services v aplikaci Visual Studio](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [Funkce podporované WCF v .NET Core](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a>Názory & dotazů

Pokud máte nějaké dotazy nebo připomínky, ohlaste je na [komunitě vývojářů](https://developercommunity.visualstudio.com/) pomocí nástroje [nahlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) .

## <a name="release-notes"></a>Zpráva k vydání verze

- Aktualizované informace o verzi, včetně známých problémů, najdete v [poznámkách k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) .
