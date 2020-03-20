---
title: 'Kurz: Vytvoření klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184104"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Kurz: Vytvoření klienta Windows Communication Foundation

Tento kurz popisuje čtvrtý z pěti úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF). Přehled výukových programů najdete v [tématu Výuka: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).

Dalším úkolem pro vytvoření aplikace WCF je vytvoření klienta načtením metadat ze služby WCF. Pomocí sady Visual Studio přidáte odkaz na službu, která získá metadata z koncového bodu MEX služby. Visual Studio pak generuje soubor spravovaného zdrojového kódu pro klientský proxy server v jazyce, který jste vybrali. Vytvoří také konfigurační soubor klienta (*App.config*). Tento soubor umožňuje klientské aplikaci připojit ke službě v koncovém bodě.

> [!NOTE]
> Pokud voláte službu WCF z projektu knihovny tříd v sadě Visual Studio, použijte funkci **Přidat odkaz na službu** k automatickému generování proxy a přidruženého konfiguračního souboru. Protože však projekty knihovny tříd tento konfigurační soubor nepoužívají, je třeba přidat nastavení v generovaném konfiguračním souboru do souboru *App.config* pro spustitelný soubor, který volá knihovnu tříd.

> [!NOTE]
> Alternativně použijte [nástroj ServiceModel Metadata Utility](#servicemodel-metadata-utility-tool) namísto Visual Studia ke generování třídy proxy a konfiguračního souboru.

Klientská aplikace používá vygenerované proxy třídy ke komunikaci se službou. Tento postup je popsán v [kurzu: Použití klienta](how-to-use-a-wcf-client.md).

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.
> - Přidejte odkaz na službu WCF pro generování třídy proxy a konfiguračních souborů.

## <a name="create-a-windows-communication-foundation-client"></a>Vytvoření klienta Windows Communication Foundation

1. Vytvoření projektu konzolové aplikace v Sadě Visual Studio:

    1. V nabídce **Soubor** vyberte **Otevřít** > **projekt/řešení** a přejděte k řešení **GettingStarted,** které jste dříve vytvořili (*GettingStarted.sln*). Vyberte **Open** (Otevřít).

    2. V nabídce **Zobrazení** vyberte **Průzkumník řešení**.

    3. V okně **Průzkumník řešení** vyberte řešení **GettingStarted** (horní uzel) a pak v místní nabídce vyberte **Přidat** > **nový projekt.**

    4. V okně **Přidat nový projekt** na levé straně vyberte kategorii Plocha **systému Windows** v části Visual **C#** nebo **Visual Basic**.

    5. Vyberte šablonu **Konzolové aplikace (.NET Framework)** a zadejte Pro **název** *příkaz GettingStartedClient* . Vyberte **OK**.

2. Přidejte odkaz v projektu **GettingStartedClient** do <xref:System.ServiceModel> sestavení:

    1. V okně **Průzkumník řešení** vyberte složku **Reference v** projektu **GettingStartedClient** a pak v místní nabídce vyberte **Přidat odkaz.**

    2. V okně **Přidat odkaz** vyberte v části **Sestavení** na levé straně okna **možnost Framework**.

    3. Najděte a vyberte **System.ServiceModel**a pak zvolte **OK**.

    4. Uložte řešení výběrem **možnosti Uložit** > **vše**.

3. Přidejte odkaz na službu kalkulačky:

   1. V okně **Průzkumník řešení** vyberte složku **Reference v** projektu **GettingStartedClient** a pak v místní nabídce vyberte **Přidat odkaz na službu.**

   2. V okně **Přidat odkaz na službu** vyberte **Zjistit**.

      Spustí se služba CalculatorService a Visual Studio ji zobrazí v poli **Služby.**

   3. Vyberte **CalculatorService** rozbalit a zobrazit servisní smlouvy implementované službou. Ponechte výchozí **obor názvů a** zvolte **OK**.

      Visual Studio přidá novou položku do složky **Připojené služby** v projektu **GettingStartedClient.**

### <a name="servicemodel-metadata-utility-tool"></a>Nástroj metadat ServiceModel

Následující příklady ukazují, jak volitelně použít [nástroj ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování souboru třídy proxy. Tento nástroj generuje soubor třídy proxy a soubor *App.config.* Následující příklady ukazují, jak generovat proxy server v jazyce C# a visual basicu:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>Konfigurační soubor klienta

Po vytvoření klienta vytvoří Visual Studio konfigurační soubor **App.config** v projektu **GettingStartedClient,** který by měl být podobný následujícímu příkladu:

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

V části [ \<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) si všimněte prvku [ \<koncového bodu>.](../configure-apps/file-schema/wcf/endpoint-element.md) Prvek ** &lt;koncového bodu&gt; ** definuje koncový bod, který klient používá pro přístup ke službě takto:

- Adresa: `http://localhost:8000/GettingStarted/CalculatorService`. Adresa koncového bodu.
- Smlouva o `ServiceReference1.ICalculator`poskytování služeb: . Servisní smlouva zpracovává komunikaci mezi klientem WCF a službou. Visual Studio vygenerovalo tuto smlouvu při použití funkce **Přidat odkaz na službu.** Je to v podstatě kopie smlouvy, kterou jste definovali v projektu GettingStartedLib.
- Vazba: <xref:System.ServiceModel.WSHttpBinding>. Vazba určuje protokol HTTP jako přenos, interoperabilní zabezpečení a další podrobnosti o konfiguraci.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.
> - Přidejte odkaz na službu WCF pro generování třídy proxy a konfiguračních souborů pro klientskou aplikaci.

Přejdete k dalšímu kurzu, kde se dozvíte, jak používat generovaného klienta.

> [!div class="nextstepaction"]
> [Kurz: Použití klienta WCF](how-to-use-a-wcf-client.md)
