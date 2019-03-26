---
title: 'Kurz: Vytvoření klienta Windows Communication Foundation'
ms.dat8: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 051275e56a8e63c6ab8136dbb9e24bdcf4c387df
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411854"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Kurz: Vytvoření klienta Windows Communication Foundation

Tento kurz popisuje čtvrté pět úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF). Přehled v kurzech, naleznete v tématu [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).

Dalším úkolem pro vytvoření aplikace WCF je vytvoření klienta načtením metadata ze služby WCF. Přidání odkazu na službu, která načte metadata z koncového bodu MEX služby pomocí sady Visual Studio. Visual Studio poté vygeneruje soubor spravovaném zdrojovém kódu pro proxy server klienta v jazyce, který jste zvolili. Také vytvoří soubor konfigurace klienta (*App.config*). Tento soubor umožňuje klientské aplikaci připojení ke službě na koncový bod. 

> [!NOTE]
> Při volání služby WCF z projektu knihovny tříd v sadě Visual Studio, použijte **přidat odkaz na službu** funkci, která automaticky generovat proxy serveru a související konfigurační soubor. Ale protože projekty knihovny tříd nepoužívejte tento konfigurační soubor, budete muset přidat nastavení v generované konfiguračního souboru k *App.config* soubor pro spustitelný soubor, který volá knihovnu tříd.

> [!NOTE]
> Jako alternativu použijte [nástroj ServiceModel Metadata Utility](#servicemodel-metadata-utility-tool) místo sady Visual Studio ke generování třídy a konfigurační soubor proxy serveru.

Klientská aplikace používá třídu proxy generovaný ke komunikaci se službou. Tento postup je popsaný v [kurzu: Používání klienta](how-to-use-a-wcf-client.md).

V tomto kurzu se naučíte:
> [!div class="checklist"]
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.
> - Přidání odkazu na službu ve službě WCF pro vygenerování souborů třídy a konfiguraci proxy serveru.


## <a name="create-a-windows-communication-foundation-client"></a>Vytvoření klienta Windows Communication Foundation

1. Vytvořte projekt konzolové aplikace v sadě Visual Studio: 

    1. Z **souboru** nabídce vyberte možnost **otevřít** > **projekt či řešení** a přejděte do **GettingStarted** řešení můžete vytvořené (*GettingStarted.sln*). Vyberte **Open** (Otevřít).

    2. Z **zobrazení** nabídce vyberte možnost **Průzkumníka řešení**.

    3. V **Průzkumníka řešení** okna, vyberte **GettingStarted** řešení (nejvyšší uzel) a pak vyberte **přidat** > **nový projekt** z místní nabídky. 
    
    4. V **přidat nový projekt** na levé straně vyberte okno **Windows Desktop** kategorie v části **Visual C#**  nebo **jazyka Visual Basic**. 

    5. Vyberte **Konzolová aplikace (.NET Framework)** šablony a zadejte *GettingStartedClient* pro **název**. Vyberte **OK**.

2. Přidat odkaz **GettingStartedClient** projektu <xref:System.ServiceModel> sestavení: 

    1.  V **Průzkumníka řešení** okna, vyberte **odkazy** ve složce **GettingStartedClient** projektu a pak vyberte **přidat odkaz** z místní nabídky. 

    2. V **přidat odkaz** okně v části **sestavení** v levé části okna vyberte **Framework**.
    
    3. Vyhledejte a vyberte **System.ServiceModel**a klikněte na tlačítko **OK**. 

    4. Uložte řešení tak, že vyberete **souboru** > **Uložit vše**.

3. Přidání odkazu na službu do kalkulačky služby:

   1. V **Průzkumníka řešení** okna, vyberte **odkazy** ve složce **GettingStartedClient** projektu a pak vyberte **přidat odkaz na službu**  z místní nabídky.

   2. V **přidat odkaz na službu** okně **Discover**.

      Spuštění služby CalculatorService a sady Visual Studio zobrazí ho v **služby** pole.

   3. Vyberte **CalculatorService** se rozbalí a zobrazí služba kontraktů implementovaných službou. Ponechte výchozí nastavení **Namespace** a zvolte **OK**.

      Přidá novou položku v sadě Visual Studio **připojené služby** složky **GettingStartedClient** projektu. 


### <a name="servicemodel-metadata-utility-tool"></a>Nástroj ServiceModel Metadata Utility

Následující příklady ukazují, jak volitelně použít [nástroj ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování souboru třídy proxy serveru. Tento nástroj generuje soubor třídy proxy a *App.config* souboru. Následující příklady ukazují, jak generovat proxy serverem v C# a Visual Basic, v uvedeném pořadí:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>Soubor konfigurace klienta

Po vytvoření klienta, vytvoří Visual Studio **App.config** v konfiguračním souboru **GettingStartedClient** projekt, který by měl vypadat přibližně jako v následujícím příkladu:

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

V části [ \<system.serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) části, Všimněte si, že [ \<koncový bod >](../configure-apps/file-schema/wcf/endpoint-element.md) elementu. **&lt;Koncový bod&gt;** definuje element koncového bodu, který klient používá pro přístup ke službě následujícím způsobem:
- Adresa: `http://localhost:8000/GettingStarted/CalculatorService`. Adresa koncového bodu.
- Kontrakt služby: `ServiceReference1.ICalculator`. Kontrakt služby zpracovává vnitřní komunikaci mezi klienta WCF a službou. Visual Studio vygeneruje tuto smlouvu, když jste použili jeho **přidat odkaz na službu** funkce. Je v podstatě kopií kontrakt, který jste definovali v projektu GettingStartedLib. 
- Vazba: <xref:System.ServiceModel.WSHttpBinding>. Vazba určuje HTTP jako přenosu, interoperabilní zabezpečení a další podrobnosti o konfiguraci.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> - Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.
> - Přidání odkazu na službu ve službě WCF ke generování proxy třída a konfigurační soubory pro klientskou aplikaci.

Přejděte k dalšímu kurzu, kde se naučíte, jak pomocí generovaného klienta.

> [!div class="nextstepaction"]
> [Kurz: Pomocí klienta WCF](how-to-use-a-wcf-client.md)


