---
title: Nástroj zprostředkovatele Microsoft WCF webové služby odkaz
description: Přehled Microsoft WCF webové služby odkaz zprostředkovatele nástroj, který přidá funkce pro .NET Core a ASP.NET Core projekty, podobně jako přidat odkaz na službu pro projekty rozhraní .NET Framework.
author: mlacouture
ms.author: johalex
ms.date: 04/19/2018
ms.custom: mvc
ms.openlocfilehash: 416ca4dbedcf6e610aa5307c87934c0cb18be749
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="microsoft-wcf-web-service-reference-provider-tool"></a>Nástroj zprostředkovatele Microsoft WCF webové služby odkaz

V průběhu let, celá řada vývojářů Visual Studio líbilo na produktivitu, [ **přidat odkaz na službu** ](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) nástroj, který poskytuje při jejich projektů rozhraní .NET Framework potřebné pro přístup k webovým službám.  **Odkaz na službu WCF Web** nástroj je rozšíření služby Visual Studio připojené, která poskytuje prostředí jako je třeba funkcionalita přidat odkaz na službu pro .NET Core a ASP.NET Core projekty. Tento nástroj získává metadata z webové služby v aktuálním řešení v umístění v síti, nebo ze souboru WSDL a vytvoří soubor kompatibilní zdroj .NET Core obsahující kód proxy serveru klienta Windows Communication Foundation (WCF), který můžete použít pro přístup k webu Služba.

> [!IMPORTANT]
> Služby by měl odkazovat jenom z důvěryhodného zdroje. Přidání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení. 

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15,5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) nebo novější verze

## <a name="how-to-use-the-extension"></a>Jak používat rozšíření

> [!NOTE]
> **Odkaz na službu WCF Web** možnost se vztahuje na projekty vytvořené pomocí následujících šablon projektu:
> * **Visual C#** > **.NET Core**
> * **Visual C#** > **Standard rozhraní .NET**
> * **Visual C#** > **webové** > **webové aplikace ASP.NET Core**

Pomocí **webové aplikace ASP.NET Core** šablony projektu jako příklad, tento článek vás provede procesem přidání odkazu na službu WCF do projektu:

1. V Průzkumníku řešení klikněte dvakrát na **připojení služby** uzel projektu (pro .NET Core nebo .NET Standard projekt tato možnost je dostupná, když klikněte pravým tlačítkem na **závislosti** uzlu projekt v Průzkumníku řešení).

**Připojené služby** stránka se zobrazí, jak je znázorněno na následujícím obrázku:

![Karta připojené služby](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Na **připojené služby** klikněte na tlačítko **odkaz zprostředkovatele služby Microsoft WCF webové služby**. Po výběru této možnosti **nastavit odkaz na službu Web WCF** průvodce:

![Karta koncový bod služby](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Vyberte službu.

    3a. Nejsou k dispozici v rámci několik možností vyhledávání služby **nastavit odkaz na službu Web WCF** průvodce:
    
     * Chcete-li vyhledat služby definované v aktuálním řešení, klikněte na tlačítko **Discover** tlačítko. 
     * K vyhledání služeb hostovaných na zadané adrese, zadejte adresu URL služby v **adresu** pole a klikněte na tlačítko **přejděte** tlačítko.
     * Chcete-li vybrat WSDL soubor, který obsahuje informace metadat webové služby, klikněte na tlačítko **Procházet** tlačítko. 
     
    3b. Zvolte ze seznamu výsledků hledání v službu **služby** pole. V případě potřeby zadejte obor názvů pro generovaný kód do odpovídajícího **Namespace** textové pole.
    
    3c. Klikněte **Další** tlačítko Otevřít **možnosti datového typu** a **možnosti klienta** stránky. Případně, kliknutím na tlačítko **Dokončit** tlačítko použít výchozí možnosti.


4. **Možnosti datového typu** formulář umožňuje Upřesnit nastavení konfigurace referenčního generovaného služby:

![Karta Možnosti typ dat](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

> [!NOTE]
> **Znovu použít typy v odkazovaných sestaveních** možnost zaškrtávací políčko je užitečné, když potřebné pro generování kódu služby referenční datové typy jsou definovány v jednom z vašeho projektu odkazované sestavení.  Je důležité znovu použít tyto existující datové typy, abyste předešli problémům s kolidovat nebo modul runtime typu v čase kompilace.

Může nastat zpoždění při načtení informací o typu, v závislosti na počtu závislosti projektu a dalších faktorů výkon systému. **Dokončit** tlačítko k dispozici při načítání, pokud **znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko je zaškrtnuté políčko.

5. Klikněte na tlačítko **Dokončit** po dokončení.


Při zobrazování průběhu nástroje:

* Stáhne metadata ze služby WCF. 
* Generuje kód odkazu služby v souboru s názvem *reference.cs*a přidá ji do projektu v části **připojené služby** uzlu. 
* Aktualizace souboru projektu (.csproj) s odkazy na balíček NuGet potřeba zkompilování a spuštění na cílové platformy.

![Průběh – okno](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Po dokončení těchto procesů, můžete vytvořit instanci typu generovaného klienta WCF a vyvolání operací služby.

## <a name="next-steps"></a>Další kroky

### <a name="feedback--questions"></a>Názory a dotazy
Pokud máte jakékoli dotazy nebo připomínky, [otevřete problém na Githubu](https://github.com/dotnet/wcf/issues/new). Můžete také zkontrolovat existující dotazy nebo problémy [v úložišti WCF na Githubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Zpráva k vydání verze
* Odkazovat [poznámky k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) aktualizované verze informace, včetně známých problémů. 
