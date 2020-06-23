---
title: 'Kurz: Vytvoření klienta Windows Communication Foundation'
description: Naučte se, jak vytvořit klienta načtením metadat ze služby WCF jako součást série článků, které vám pomůžou začít vytvářet aplikace WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d5a2a2b5175c9e34eaf1dbaff20ac57f34117c4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246321"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Kurz: Vytvoření klienta Windows Communication Foundation

Tento kurz popisuje čtvrtý z pěti úkolů potřebných k vytvoření aplikace Basic Windows Communication Foundation (WCF). Přehled kurzů najdete v tématu [kurz: Začínáme s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).

Další úlohou pro vytvoření aplikace WCF je vytvoření klienta načtením metadat ze služby WCF. Pomocí sady Visual Studio můžete přidat odkaz na službu, který získá metadata z koncového bodu služby MEX. Visual Studio potom vygeneruje spravovaný soubor zdrojového kódu pro proxy klienta v jazyce, který jste zvolili. Zároveň vytvoří konfigurační soubor klienta (*App.config*). Tento soubor umožňuje klientské aplikaci připojit se ke službě na koncovém bodu.

> [!NOTE]
> Pokud voláte službu WCF z projektu knihovny tříd v aplikaci Visual Studio, použijte funkci **Přidat odkaz na službu** k automatickému vygenerování proxy a přidruženého konfiguračního souboru. Nicméně vzhledem k tomu, že projekty knihovny tříd nepoužívají tento konfigurační soubor, je nutné přidat nastavení do generovaného konfiguračního souboru do souboru *App.config* pro spustitelný soubor, který volá knihovnu tříd.

> [!NOTE]
> K vygenerování třídy proxy a konfiguračního souboru místo sady Visual Studio můžete použít také nástroj pro použití [metadat ServiceModel](#servicemodel-metadata-utility-tool) .

Klientská aplikace používá vygenerovanou třídu proxy ke komunikaci se službou. Tento postup je popsaný v tématu [kurz: použití klienta](how-to-use-a-wcf-client.md).

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.
> - Přidejte odkaz na službu služby WCF, který vygeneruje proxy třídu a konfigurační soubory.

## <a name="create-a-windows-communication-foundation-client"></a>Vytvoření klienta Windows Communication Foundation

1. Vytvoření projektu konzolové aplikace v aplikaci Visual Studio:

    1. V nabídce **soubor** vyberte **otevřít**  >  **projekt/řešení** a přejděte k **soubor GettingStarted** řešení, které jste dříve vytvořili (*soubor GettingStarted. sln*). Vyberte **Open** (Otevřít).

    2. V nabídce **zobrazení** vyberte **Průzkumník řešení**.

    3. V okně **Průzkumník řešení** vyberte řešení **soubor GettingStarted** (nejvyšší uzel) a pak v místní nabídce vyberte **Přidat**  >  **Nový projekt** .

    4. V okně **Přidat nový projekt** na levé straně vyberte kategorii **Desktop systému Windows** v části **Visual C#** nebo **Visual Basic**.

    5. Vyberte šablonu **Konzolová aplikace (.NET Framework)** a jako **název**zadejte *GettingStartedClient* . Vyberte **OK**.

2. Přidejte odkaz do projektu **GettingStartedClient** do <xref:System.ServiceModel> sestavení:

    1. V okně **Průzkumník řešení** vyberte složku **odkazy** v projektu **GettingStartedClient** a pak vyberte **Přidat odkaz** z místní nabídky.

    2. V okně **Přidat odkaz** v části **sestavení** na levé straně okna vyberte možnost **Architektura**.

    3. Vyhledejte a vyberte **System. ServiceModel**a pak zvolte **OK**.

    4. Uložte řešení tak, že vyberete **soubor**  >  **Uložit vše**.

3. Přidejte do služby kalkulačky odkaz na službu:

   1. V okně **Průzkumník řešení** vyberte složku **odkazy** v projektu **GettingStartedClient** a potom v místní nabídce vyberte **Přidat odkaz na službu** .

   2. V okně **Přidat odkaz na službu** vyberte **zjistit**.

      Služba CalculatorService se spustí a aplikace Visual Studio je zobrazí v poli **služby** .

   3. Vyberte **CalculatorService** a rozbalte ji a zobrazte kontrakty služeb implementované službou. Ponechte výchozí **obor názvů** a klikněte na **tlačítko OK**.

      Visual Studio přidá novou položku do složky **připojené služby** v projektu **GettingStartedClient** .

### <a name="servicemodel-metadata-utility-tool"></a>Nástroj pro metadata ServiceModel

V následujících příkladech se dozvíte, jak volitelně pomocí nástroje pro generování [metadat třídy ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) vytvořit soubor třídy proxy. Tento nástroj generuje soubor třídy proxy a soubor *App.config* . Následující příklady ukazují, jak vygenerovat proxy v jazyce C# a Visual Basic v uvedeném pořadí:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>Konfigurační soubor klienta

Po vytvoření klienta Visual Studio vytvoří konfigurační soubor **App.config** v projektu **GettingStartedClient** , který by měl být podobný následujícímu příkladu:

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

V [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) části si všimněte [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) elementu. Element ** &lt; Endpoint &gt; ** definuje koncový bod, který klient používá pro přístup ke službě, následovně:

- Adresa: `http://localhost:8000/GettingStarted/CalculatorService` . Adresa koncového bodu.
- Kontrakt služby: `ServiceReference1.ICalculator` . Kontrakt služby zajišťuje komunikaci mezi klientem WCF a službou. Aplikace Visual Studio vygenerovala tento kontrakt při použití funkce **Přidat odkaz na službu** . Je v podstatě kopie smlouvy, kterou jste definovali v projektu GettingStartedLib.
- Vazba: <xref:System.ServiceModel.WSHttpBinding> . Vazba určí protokol HTTP jako přenos, prointeroperabilní zabezpečení a další podrobnosti o konfiguraci.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.
> - Přidejte odkaz na službu služby WCF, který vygeneruje proxy třídu a konfigurační soubory pro klientskou aplikaci.

Přejděte k dalšímu kurzu, kde se dozvíte, jak používat vygenerovaný klient.

> [!div class="nextstepaction"]
> [Kurz: použití klienta WCF](how-to-use-a-wcf-client.md)
