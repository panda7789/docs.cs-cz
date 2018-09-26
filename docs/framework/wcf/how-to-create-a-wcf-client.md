---
title: 'Postupy: Vytvoření klienta Windows Communication Foundation'
ms.date: 09/14/2018
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 1eadb5008575a1a53d685db14d68e42d0dce1360
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070673"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Postupy: Vytvoření klienta Windows Communication Foundation

Toto je čtvrtý z šesti úkolů potřebný k vytvoření aplikace Windows Communication Foundation (WCF). Přehled všech šesti úkoly, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.

Toto téma popisuje, jak načíst metadata ze služby WCF a použijte ji k vytvoření proxy WCF, které můžete přístup ke službě. Tuto úlohu provedete pomocí **přidat odkaz na službu** funkce poskytované službou Visual Studio. Tento nástroj získává metadata z koncového bodu služby MEX a vygeneruje soubor spravovaném zdrojovém kódu pro proxy server klienta v jazyce rozhodli (C# ve výchozím nastavení). Kromě vytvoření proxy serveru klienta, nástroj také vytvoří nebo aktualizuje konfigurační soubor klienta, která umožňuje klientské aplikaci připojení ke službě na jeden z jeho koncových bodů.

> [!NOTE]
> Můžete také použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj pro generování třídy proxy serveru a konfigurace namísto použití **přidat odkaz na službu** v sadě Visual Studio.

> [!NOTE]
> Při volání služby WCF z projektu knihovny tříd v sadě Visual Studio, můžete použít **přidat odkaz na službu** funkci, která automaticky generovat proxy serveru a související konfigurační soubor. Konfigurační soubor se nepoužije projekt knihovny tříd. Budete muset přidat nastavení v souboru vygenerovanou konfiguraci do souboru app.config pro spustitelný soubor, který volá knihovnu tříd.

Klientská aplikace používá třídu proxy generovaný ke komunikaci se službou. Tento postup je popsaný v [postupy: používání klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).

## <a name="to-create-a-windows-communication-foundation-client"></a>K vytvoření klienta Windows Communication Foundation

1. Vytvořte nový projekt konzolové aplikace v sadě Visual Studio. Klikněte pravým tlačítkem na řešení Začínáme v **Průzkumníka řešení** a vyberte **přidat** > **nový projekt**. V **přidat nový projekt** dialogového okna na levé straně, vyberte **Windows Desktop** kategorie v části **Visual C#** nebo **jazyka Visual Basic**. Vyberte **Konzolová aplikace (.NET Framework)** šablony a poté pojmenujte projekt **GettingStartedClient**.

2. Přidáte odkaz na System.ServiceModel GettingStartedClient projektu. Klikněte pravým tlačítkem na **odkazy** ve složce projektu GettingStartedClient v **Průzkumníka řešení**a pak vyberte **přidat odkaz**. V **přidat odkaz** dialogového okna, vyberte **Framework** na levé straně dialogového okna v části **sestavení**. Vyhledejte a vyberte **System.ServiceModel**a klikněte na tlačítko **OK**. Uložte řešení tak, že vyberete **souboru** > **Uložit vše**.

3. Přidání odkazu na službu ve službě kalkulačku.

   1. Nejprve spusťte GettingStartedHost konzolové aplikace.

   2. Po spuštění hostitele, klikněte pravým tlačítkem **odkazy** ve složce projektu GettingStartedClient v **Průzkumníku řešení** a vyberte **přidat**  >   **Odkaz na službu**.

   3. Do pole Adresa zadejte následující adresu URL **přidat odkaz na službu** dialogové okno: [http://localhost:8000/GettingStartedClient/Service](http://localhost:8000/GettingStartedClient/Service)

   4. Zvolte **Přejít**.

   Se zobrazí CalculatorService **služby** pole se seznamem. Dvakrát klikněte na panel CalculatorService se rozbalí a zobrazí služba kontraktů implementovaných službou. Ponechte výchozí obor názvů jako- a zvolíte **OK**.

    Když přidáte odkaz na službu pomocí sady Visual Studio, objeví nová položka v **Průzkumníka řešení** pod **odkazy na služby** GettingStartedClient projektu ve složce. Pokud používáte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) jsou generovány nástroj, zdrojový soubor a soubor app.config.

    Můžete také použít nástroj příkazového řádku [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pomocí příslušných přepínačů vytvořte klientský kód. Následující příklad generuje soubor kódu a konfiguračním souboru služby. První příklad ukazuje, jak generovat proxy serveru v jazyce Visual Basic a druhý ukazuje, jak generovat proxy serveru v jazyce C#:

    ```shell
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

    ```shell
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

## <a name="next-steps"></a>Další kroky

Vytvořili jste proxy server, který klientská aplikace bude používat k volání služby kalkulačku. Pokračujte k dalšímu tématu, v řadě.

> [!div class="nextstepaction"]
> [Postupy: Konfigurace klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

## <a name="see-also"></a>Viz také:

- [Nástroj metadat modelu služby (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)
- [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
