---
title: Ukázky vytváření Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: b6b541b93661f3da656e36d65ef3f94d76cae0c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658868"
---
# <a name="building-the-windows-communication-foundation-samples"></a>Ukázky vytváření Windows Communication Foundation

Ukázky Windows Communication Foundation (WCF) může být sestaven pomocí integrovaného vývojového prostředí sady Visual Studio nebo **msbuild** příkazu z příkazového řádku. Oba postupy jsou popsané v tomto tématu.

> [!NOTE]
> Před vytvářejí nebo s některým z ukázky WCF, ujistěte, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

## <a name="to-build-the-sample-using-a-command-prompt"></a>K vytvoření vzorku pomocí příkazového řádku

1.  Otevřete Developer Command Prompt pro sadu Visual Studio a přejděte do podadresáře konkrétní jazyk v části umístění adresáře, kam jste nainstalovali vzorku.

2.  Typ `msbuild` na příkazovém řádku. Programové soubory nástroje klienta jsou integrované do *client\bin* a programové soubory nástroje služby jsou integrované do *service\bin*. Pokud služba je hostována v Internetové informační služby (IIS), programové soubory nástroje služby jsou zkopírovány také do *servicemodelsamples* adresáře a jeho *\bin* podadresáře.

> [!NOTE]
> Je potřeba nastavit seznamy ACL v *%systemdrive%\inetpub\wwwroot* udělit změnit oprávnění k účtu, pod kterým běží. V opačném případě některé publikovat události selhání sestavení. Alternativně můžete nechat seznamy ACL, jak jsou a spustit jako správce příkazový řádek sady SDK.

## <a name="to-build-the-sample-using-visual-studio"></a>K vytvoření vzorku pomocí sady Visual Studio

1. Z **souboru** nabídky v sadě Visual Studio, vyberte **otevřít** > **projekt či řešení**. Přejděte do podadresáře konkrétní jazyk v adresáři, do které jste nainstalovali vzorku a dvakrát klikněte na ikonu souboru .sln k otevření řešení v sadě Visual Studio.

1. Z **sestavení** nabídce vyberte možnost **znovu sestavit řešení**.

   Programové soubory nástroje klienta jsou integrované do client\bin a programové soubory nástroje služby jsou integrované do service\bin. Pokud služba je hostována ve službě IIS, programové soubory nástroje služby jsou zkopírovány také do *servicemodelsamples* adresáře a jeho *\bin* podadresáře.

> [!NOTE]
> Je potřeba nastavit seznamy ACL v %systemdrive%\inetpub\wwwroot udělit změnit oprávnění k účtu, pod kterým běží. V opačném případě některé publikovat události selhání sestavení. Alternativně můžete nechat seznamy ACL, jak jsou a spustit příkazový řádek sady SDK nebo Visual Studio jako správce. Některé akce sady Visual Studio (jako je připojení ladicího programu k pracovnímu procesu ASP.Net) také vyžadují oprávnění správce.

## <a name="setup-batch-files-and-scripts"></a>Instalační program dávkové soubory a skripty
 Setup.exe a Cleanup.exe dávkové soubory a skripty je vhodné spustit z příkazového řádku pro vývojáře pro sadu Visual Studio. Několik set up a čištění souborů provádět úlohy, které vyžadují oprávnění správce a má být spuštěna s oprávněním správce.

## <a name="important-security-information-about-metadata-endpoints"></a>Důležité informace o zabezpečení o koncové body metadat
 Pokud chcete zabránit neúmyslnému zveřejnění metadat služby potenciálně citlivých, výchozí konfigurace pro služby Windows Communication Foundation (WCF) zakáže publikování metadat. Toto chování je ve výchozím nastavení zabezpečený, ale také znamená, že nemůžete použít metadat importovat nástroj (například Svcutil.exe) ke generování kódu klienta, který je potřeba volat službu, není-li v konfiguraci není explicitně povoleno chování publikování metadat služby. Aby experimentování s ukázkami jednodušší, zveřejnit téměř všechny ukázky koncový bod publikování nezabezpečené metadat. Tyto koncové body jsou potenciálně dostupné pro anonymní neověřené uživatele a musí tak, aby byl veřejně pocházejí metadata služby odpovídající věnovat pozornost před nasazením tyto koncové body. Další informace o publikování metadat služby, najdete v článku [chování publikování metadat](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) vzorku. Najdete v článku [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) ukázka ukázku zabezpečení koncových bodů metadat.

## <a name="exception-handling"></a>Zpracování výjimek
 Obecně řečeno tyto ukázky neobsahují kód, zaměřuje na předmět ukázky zpracování výjimek. Další informace o zpracování výjimek naleznete v tématu [očekávané výjimky](../../../../docs/framework/wcf/samples/expected-exceptions.md) vzorku.

## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Znova se generuje klienty a konfiguraci s Svcutil
 Můžete použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) se znova vygenerovat kód klienta a konfigurace pro většinu z ukázek. Některé ukázky vyžadují ručně upravené konfigurace. Například pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace ukázku, která používá přihlašovací údaje pro klienta certifikát, musíte ručně zadat přihlašovací údaje, které jste dříve nakonfigurovali. Některé ukázky použít specifické možnosti Svcutil.exe ovlivnit generovaného kódu, tyto možnosti se uvádějí ve vzorku konkrétní témata.

### <a name="to-regenerate-the-client-and-configuration-files"></a>Znovu vygenerovat klienta a konfigurační soubory

1.  Otevřete příkazový řádek sady SDK a přejděte do podadresáře konkrétní jazyk v části umístění adresáře, kam jste nainstalovali vzorku.

2.  Pokud je služba Web hostovaný typ, použijte následující příkaz.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Pokud je služba v místním prostředí zadáním následujícího příkazu.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Nahraďte `http://localhost:8000/ServiceModelSamples/service.svc/mex` adresu koncového bodu mex služba v místním prostředí.

     Ke generování klienta v jazyce Visual Basic typu, použijte následující příkaz.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     Pokud je služba typu v místním prostředí, použijte následující příkaz.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > Chcete-li přeskočit generování konfigurace klienta přidat **/noconfig** možnost.

## <a name="see-also"></a>Viz také:

- [Spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md)
- [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
