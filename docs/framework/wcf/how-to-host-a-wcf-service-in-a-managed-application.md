---
title: 'Postupy: Hostování služby WCF ve spravované aplikaci'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: e3adcad6ba70aa64b797325cd45a043301d7e680
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320981"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>Postupy: hostování služby WCF ve spravované aplikaci

Chcete-li hostovat službu uvnitř spravované aplikace, vložte kód pro službu do spravovaného kódu aplikace, Definujte koncový bod pro službu buď imperativně v kódu, deklarativně prostřednictvím konfigurace, nebo pomocí výchozích koncových bodů, a pak vytvořte instance <xref:System.ServiceModel.ServiceHost>.

Chcete-li zahájit přijímání zpráv, zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>. Tím se vytvoří a otevře se naslouchací proces pro službu. Hostování služby tímto způsobem se často označuje jako "samoobslužné hostování", protože spravovaná aplikace provádí hostující práci sama. Chcete-li službu zavřít, zavolejte <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost>.

Službu je také možné hostovat ve spravované službě Windows, v Internetová informační služba (IIS) nebo ve službě WAS (Windows Process Activation Service). Další informace o možnostech hostování pro službu najdete v tématu [hostingové služby](hosting-services.md).

Hostování služby ve spravované aplikaci je nejpružnější možnost, protože pro nasazení vyžaduje minimální infrastrukturu. Další informace o hostitelských službách ve spravovaných aplikacích najdete v tématu [hostování ve spravované aplikaci](./feature-details/hosting-in-a-managed-application.md).

Následující postup ukazuje, jak implementovat samoobslužnou službu v konzolové aplikaci.

## <a name="create-a-self-hosted-service"></a>Vytvoření samoobslužné služby

1. Vytvořit novou konzolovou aplikaci:

   1. Otevřete Visual Studio a v nabídce **soubor** vyberte **Nový** **projekt**  > .

   2. V seznamu **Nainstalované šablony** vyberte možnost **Visual C#**  nebo **Visual Basic**a pak vyberte možnost **desktopová plocha systému Windows**.

   3. Vyberte šablonu **Konzolová aplikace** . Do pole **název** zadejte `SelfHost` a pak zvolte **OK**.

2. V **Průzkumník řešení** klikněte pravým tlačítkem na **SelfHost** a vyberte **Přidat odkaz**. Na kartě **.NET** vyberte **System. ServiceModel** a pak zvolte **OK**.

    > [!TIP]
    > Pokud není okno **Průzkumník řešení** viditelné, vyberte v nabídce **zobrazení** položku **Průzkumník řešení** .

3. Poklikejte na **program.cs** nebo **Module1. vb** v **Průzkumník řešení** pro otevření v okně kódu, pokud už není otevřený. Na začátek souboru přidejte následující příkazy:

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. Definování a implementace kontraktu služby. Tento příklad definuje `HelloWorldService`, který vrátí zprávu na základě vstupu do služby.

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > Další informace o tom, jak definovat a implementovat rozhraní služby, naleznete v tématu [How to: define](how-to-define-a-wcf-service-contract.md) a Service kontrakt a [How to: Implement kontraktu služby](how-to-implement-a-wcf-contract.md).

5. V horní části metody @no__t 0 vytvořte instanci třídy <xref:System.Uri> se základní adresou pro službu.

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. Vytvořte instanci třídy <xref:System.ServiceModel.ServiceHost> a předejte <xref:System.Type> reprezentující typ služby a základní adresu identifikátoru URI (Uniform Resource Identifier) na <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Povolte publikování metadat a potom zavolejte metodu <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost> pro inicializaci služby a připravte ji na příjem zpráv.

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > Tento příklad používá výchozí koncové body a pro tuto službu není vyžadován žádný konfigurační soubor. Pokud nejsou nakonfigurovány žádné koncové body, modul runtime vytvoří jeden koncový bod pro každou základní adresu pro každý kontrakt služby implementovaný službou. Další informace o výchozích koncových bodech najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).

7. Pro sestavení řešení stiskněte **Ctrl**+**SHIFT**+**B** .

## <a name="test-the-service"></a>Testování služby

1. Stisknutím **kombinace kláves Ctrl**+**F5** službu spusťte.

2. Otevřete **testovacího klienta WCF**.

    > [!TIP]
    > Chcete-li otevřít **klienta služby WCF test**, otevřete Developer Command Prompt pro Visual Studio a spusťte **WcfTestClient. exe**.

3. V nabídce **soubor** vyberte **Přidat službu** .

4. Do pole Adresa zadejte `http://localhost:8080/hello` a klikněte na **OK**.

    > [!TIP]
    > Ujistěte se, že je služba spuštěná, nebo jinak tento krok neproběhne úspěšně. Pokud jste v kódu změnili základní adresu, použijte v tomto kroku upravenou základní adresu.

5. Dvakrát klikněte na **sayHello** pod uzlem **Moje projekty služeb** . Do sloupce **hodnota** v seznamu **požadavků** zadejte své jméno a klikněte na **vyvolat**.

   V seznamu **odpovědí** se zobrazí zpráva s odpovědí.

## <a name="example"></a>Příklad

Následující příklad vytvoří objekt <xref:System.ServiceModel.ServiceHost> pro hostování služby typu `HelloWorldService` a potom zavolá metodu <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>. V kódu je uvedena základní adresa, publikování metadat je povoleno a jsou použity výchozí koncové body.

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>Viz také:

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [Postupy: Hostování služby WCF v IIS](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Vlastní hostování](./samples/self-host.md)
- [Služby hostování](hosting-services.md)
- [Postupy: Definování kontraktu služby](how-to-define-a-wcf-service-contract.md)
- [Postupy: Implementace kontraktu služby](how-to-implement-a-wcf-contract.md)
- [Nástroj metadat modelu služby (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
- [Vazby poskytované systémem](system-provided-bindings.md)
