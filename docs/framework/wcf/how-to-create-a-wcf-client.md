---
title: 'Postupy: Vytvoření klienta Windows Communication Foundation'
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 9e6d75bf8911a3c36e63b3bc108faae823434d1d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397286"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Postupy: Vytvoření klienta Windows Communication Foundation

Toto je čtvrtý z šesti úkolů potřebný k vytvoření aplikace Windows Communication Foundation (WCF). Přehled všech šesti úkoly, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.

Toto téma popisuje, jak načíst metadata ze služby WCF a použijte ji k vytvoření proxy WCF, které můžete přístup ke službě. Tuto úlohu provedete pomocí funkce Přidat odkaz na službu poskytovaný sadou Visual Studio. Tento nástroj získává metadata z koncového bodu služby MEX a vygeneruje soubor spravovaném zdrojovém kódu pro proxy server klienta v jazyce rozhodli (C# ve výchozím nastavení). Kromě vytvoření proxy serveru klienta, nástroj také vytvoří nebo aktualizuje konfigurační soubor klienta, která umožňuje klientské aplikaci připojení ke službě na jeden z jeho koncových bodů.

> [!NOTE]
> Můžete také použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj pro generování třídy proxy serveru a konfigurace namísto použití přidat odkaz na službu v aplikaci Visual Studio.

> [!WARNING]
> Při volání služby WCF z projektu knihovny tříd v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] automaticky generovat proxy serveru a související konfigurační soubor můžete použít funkci Přidat odkaz na službu.  Konfigurační soubor se nepoužije projekt knihovny tříd. Je potřeba přidat nastavení v souboru vygenerovanou konfiguraci do souboru app.config pro spustitelný soubor, který bude volat knihovně tříd rozhraní.

 Klientská aplikace používá třídu proxy generovaný ke komunikaci se službou. Tento postup je popsaný v [postupy: používání klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).

## <a name="to-create-a-windows-communication-foundation-client"></a>K vytvoření klienta Windows Communication Foundation

1.  Vytvořit nový projekt konzolové aplikace kliknutím pravým tlačítkem na řešení Začínáme vyberete, **přidat**, **nový projekt**. V **přidat nový projekt** dialogového okna na levé straně dialogového okna vyberte **Windows** pod **jazyka C#** nebo **VB**. V části System center dialogového okna vyberte **konzolovou aplikaci**. Pojmenujte projekt `GettingStartedClient`.

2.  Nastavte cílovou architekturu projektu GettingStartedClient na rozhraní .NET Framework 4.5 kliknutím pravým tlačítkem na **GettingStartedClient** v Průzkumníku řešení a vyberete **vlastnosti**. V rozevíracím seznamu s názvem **Cílová architektura** vyberte **rozhraní .NET Framework 4.5**. Nastavení cílové rozhraní projektu VB je trochu jiné, v dialogovém okně Vlastnosti projektu GettingStartedClient, klikněte na tlačítko **kompilaci** kartu na levé straně obrazovky a pak klikněte na tlačítko **Upřesnit Možnosti kompilace** tlačítko v levém dolním rohu dialogového okna. Potom vyberte **rozhraní .NET Framework 4.5** v rozevíracím seznamu s názvem **Cílová architektura**.

     Nastavení cílové architektury způsobí Visual Studio 2011 znovu načíst řešení a stiskněte klávesu **OK** po zobrazení výzvy.

3.  Přidat odkaz na System.ServiceModel GettingStartedClient projektu kliknutím pravým tlačítkem myši **odkaz** ve složce GettingStartedClient projekt v Průzkumníku řešení a vyberte **přidat** Referenční dokumentace. V **přidat odkaz** dialogové okno Vybrat **Framework** na levé straně dialogového okna. Do textového pole hledání sestavení, zadejte v `System.ServiceModel`. V části System center dialogového okna vyberte **System.ServiceModel**, klikněte na tlačítko **přidat** tlačítko a klikněte na tlačítko **Zavřít** tlačítko. Uložte řešení kliknutím **Uložit vše** tlačítko níže v hlavní nabídce.

4.  Dále přidáte odkaz na službu ve službě kalkulačku. Předtím, než budete moct provést, je nutné spustit aplikaci GettingStartedHost konzoly. Po spuštění hostitele, klikněte pravým tlačítkem **odkazy** ve složce projektu GettingStartedClient v **Průzkumníku řešení** a vyberte **přidat**  >   **Odkaz na službu**. Zadejte následující adresu URL do pole adresy **přidat odkaz na službu** dialogového okna: [ http://localhost:8000/ServiceModelSamples/Service ](http://localhost:8000/ServiceModelSamples/Service) a klikněte na tlačítko **přejděte** tlačítko. CalculatorService by pak zobrazí v seznamu služeb. Dvakrát klikněte na panel CalculatorService a bude rozbalit a zobrazit služby kontraktů implementovaných službou. Ponechte výchozí obor názvů, jak jsou a klikněte na tlačítko **OK** tlačítko.

     Když přidáte odkaz na službu pomocí sady Visual Studio nové položky se zobrazí v Průzkumníku řešení ve složce odkazy na služby v rámci projektu GettingStartedClient.  Pokud používáte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj se vygeneruje soubor zdrojového kódu a soubor app.config.

     Můžete také použít nástroj příkazového řádku [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pomocí příslušných přepínačů vytvořte klientský kód. Následující příklad generuje soubor kódu a konfiguračním souboru služby. První příklad ukazuje, jak generovat proxy serveru v jazyce Visual Basic a druhá ukazuje, jak vytvořit proxy serveru v jazyce C#:

    ```
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service
    ```

    ```csharp
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service
    ```

 Nyní jste vytvořili proxy server, který klientská aplikace bude používat k volání služby kalkulačku. Pokračovat k dalšímu tématu, v této sérii: [postupy: Konfigurace klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

## <a name="see-also"></a>Viz také

- [Nástroj metadat modelu služby (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)
- [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
