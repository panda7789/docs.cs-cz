---
title: 'Postupy: Konfigurace klienta základní Windows Communication Foundation'
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 3f267edf87711de8a5969e3e0b577648008c5a75
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562187"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>Postupy: Konfigurace klienta základní Windows Communication Foundation

Toto je pátý šesti úkolů, muset vytvořit základní aplikaci Windows Communication Foundation (WCF). Přehled všech šesti úkoly, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.

Toto téma popisuje klientské konfigurační soubor, který se vygeneroval pomocí **přidat odkaz na službu** funkce sady Visual Studio nebo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Konfigurace klienta se skládá z zadání koncového bodu, který klient používá pro přístup ke službě. Koncový bod má adresa, vazba a kontrakt a každý z nich musí být zadán právě konfigurace klienta.

## <a name="configure-a-windows-communication-foundation-client"></a>Konfigurace klienta Windows Communication Foundation

Z projektu GettingStartedClient otevřete vygenerovaný konfigurační soubor (App.config). V následujícím příkladu je zobrazení generovaného konfiguračního souboru. V části [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) části, vyhledejte [ \<koncový bod >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
          <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />
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
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

Tento příklad konfiguruje koncového bodu, který klient používá pro přístup ke službě, která se nachází na následující adrese: `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`.

Určuje element koncového bodu, který `ServiceReference1.ICalculator` kontraktu služby se používá ke komunikaci mezi klienta WCF a službou. Kanál WCF se nakonfigurují poskytovaných systémem <xref:System.ServiceModel.WSHttpBinding>. Tato smlouva byl vytvořen pomocí **přidat odkaz na službu** v sadě Visual Studio. Je v podstatě kopií, která byla definována v projektu GettingStartedLib kontrakt. <xref:System.ServiceModel.WSHttpBinding> Vazbu určuje HTTP jako přenosu, interoperabilní zabezpečení a další podrobnosti o konfiguraci.

Další informace o tom, jak pomocí generovaného klienta s touto konfigurací najdete v tématu [postupy: používání klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Postupy: používání klienta WCF](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

## <a name="see-also"></a>Viz také:

- [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Nástroj metadat modelu služby (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Postupy: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)