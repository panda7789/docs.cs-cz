---
title: Ukázky vytváření Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: 021f17778bc019828d00fbd8e93cbc319de3047a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990157"
---
# <a name="building-the-windows-communication-foundation-samples"></a>Ukázky vytváření Windows Communication Foundation

Ukázky Windows Communication Foundation (WCF) lze sestavit pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio nebo pomocí příkazu **MSBuild** z příkazového řádku. Oba postupy jsou popsány v tomto tématu.

> [!NOTE]
> Před vytvořením nebo spuštěním kterékoli z ukázek služby WCF se ujistěte, že jste provedli [jednorázovou proceduru nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

## <a name="to-build-the-sample-using-a-command-prompt"></a>Postup sestavení ukázky pomocí příkazového řádku

1. Otevřete Developer Command Prompt pro Visual Studio a přejděte do podadresáře pro konkrétní jazyk v umístění adresáře, kam jste si nainstalovali ukázku.

2. Do `msbuild` příkazového řádku zadejte. Soubory klientských programů jsou sestaveny tak, aby *client\bin* a programové soubory služby jsou sestaveny tak, aby *service\bin*. Pokud je služba hostovaná službou Internetová informační služba (IIS), soubory programu služby se zkopírují i do adresáře *ServiceModelSamples* a jeho podadresáře *\Bin* .

> [!NOTE]
> Je nutné nastavit seznamy ACL pro *%systemdrive%\Inetpub\Wwwroot* tak, aby udělily oprávnění k úpravám účtu, pod kterým je spuštěný. Jinak některé události po sestavení selžou. Případně můžete seznamy ACL ponechat tak, jak jsou, a spustit příkazový řádek sady SDK jako správce.

## <a name="to-build-the-sample-using-visual-studio"></a>K vytvoření vzorku pomocí sady Visual Studio

1. V nabídce **soubor** v aplikaci Visual Studio vyberte **otevřít** > **projekt/řešení**. Přejděte do podadresáře pro konkrétní jazyk v adresáři, ve kterém jste nainstalovali ukázku, a dvakrát klikněte na ikonu souboru. sln a otevřete řešení v aplikaci Visual Studio.

1. V nabídce **sestavení** vyberte znovu **Sestavit řešení**.

   Soubory klientských programů jsou sestaveny tak, aby client\bin a programové soubory služby jsou sestaveny tak, aby service\bin. Pokud je služba hostovaná ve službě IIS, soubory programu služby se zkopírují i do adresáře *ServiceModelSamples* a jeho podadresáře *\Bin* .

> [!NOTE]
> Je nutné nastavit seznamy ACL pro%systemdrive%\Inetpub\Wwwroot tak, aby udělily oprávnění k úpravám účtu, pod kterým je spuštěný. Jinak některé události po sestavení selžou. Případně můžete seznamy ACL ponechat tak, jak jsou, a spustit příkazový řádek sady SDK nebo sadu Visual Studio jako správce. Některé akce sady Visual Studio (například připojení ladicího programu k pracovnímu procesu ASP.Net) vyžadují také oprávnění správce.

## <a name="setup-batch-files-and-scripts"></a>Nastavení dávkových souborů a skriptů
 Soubory Setup. exe a Cleanup. exe Batch a skripty by se měly spouštět z Developer Command Prompt pro Visual Studio. Několik nastavení a vyčištění souborů provádí úlohy, které vyžadují oprávnění správce a měly by být spouštěny s oprávněními správce.

## <a name="important-security-information-about-metadata-endpoints"></a>Důležité informace o zabezpečení pro koncové body metadat
 Aby nedocházelo k neúmyslnému zveřejnění potenciálně citlivých metadat služby, služba výchozí konfigurace služby Windows Communication Foundation (WCF) zakáže publikování metadat. Toto chování je standardně zabezpečené, ale také znamená, že nemůžete použít nástroj pro import metadat (například Svcutil. exe), aby se vygeneroval kód klienta vyžadovaný pro volání služby, pokud není v konfiguraci explicitně povolený chování publikování metadat služby. Téměř všechny ukázky vystavují nezabezpečený koncový bod publikování metadat, aby bylo experimentování s ukázkami snazší. Tyto koncové body jsou možná dostupné anonymním neověřeným příjemcům a před nasazením těchto koncových bodů je nutné zajistit, aby bylo zajištěno, že bude jejich veřejněné zveřejnění metadat služby vhodné. Další informace o publikování metadat služby najdete v ukázce [chování publikování metadat](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) . Ukázku zabezpečení koncového bodu metadat najdete v ukázce pro [Vlastní zabezpečený koncový bod metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) .

## <a name="exception-handling"></a>Zpracování výjimek
 Obecně řečeno tyto ukázky nezahrnují zpracování výjimek, aby se kód zaměřil na předmět ukázky. Další informace o zpracování výjimek naleznete v ukázce [očekávaných výjimek](../../../../docs/framework/wcf/samples/expected-exceptions.md) .

## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Opětovné generování klientů a konfigurace pomocí Svcutil
 K opětovnému vygenerování kódu a konfigurace klienta pro většinu ukázek můžete použít nástroj pro dodávání [metadat (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) . Některé ukázky vyžadují ruční úpravu konfigurace. Pokud například pomocí Svcutil. exe znovu vygenerujete konfiguraci pro ukázku, která používá přihlašovací údaje klientského certifikátu, musíte ručně zadat přihlašovací údaje, které jste nakonfigurovali dříve. Některé ukázky používají konkrétní možnosti Svcutil. exe, které mají vliv na generovaný kód. tyto možnosti jsou uvedeny v konkrétních ukázkových tématech.

### <a name="to-regenerate-the-client-and-configuration-files"></a>Obnovení klientského a konfiguračního souboru

1. Otevřete příkazový řádek sady SDK a přejděte do podadresáře pro konkrétní jazyk v umístění adresáře, kam jste si nainstalovali ukázku.

2. Pokud je služba typu na webu, použijte následující příkaz.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Pokud je služba místně hostovaná, zadejte následující příkaz.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Nahraďte `http://localhost:8000/ServiceModelSamples/service.svc/mex` adresou koncového bodu mex samoobslužné služby.

     K vygenerování klienta v typu Visual Basic použijte následující příkaz.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     Pokud je tato služba samoobslužným typem, použijte následující příkaz.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > Pokud chcete přeskočit generování konfigurace klienta, přidejte možnost **/noconfig** .

## <a name="see-also"></a>Viz také:

- [Spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md)
- [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
