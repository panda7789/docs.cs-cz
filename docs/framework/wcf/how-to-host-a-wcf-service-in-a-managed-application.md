---
title: 'Postupy: Hostování služby WCF ve spravované aplikaci'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: b6d1c9c38e2cc5f1b1b7b5538af0339987563de6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637583"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>Postupy: Hostování služby WCF ve spravované aplikaci

Hostování služby do spravované aplikace, kód služby do spravované aplikace kódu pro vložení, definovat koncový bod pro službu buď imperativně v kódu, deklarativně pomocí konfigurace nebo pomocí výchozí koncové body a pak vytvořte instance <xref:System.ServiceModel.ServiceHost>.

Chcete-li začít přijímat zprávy, zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>. Tím se vytvoří a otevře naslouchacího procesu pro službu. Hostitelská služba tímto způsobem se často označuje jako "hostování na vlastním" protože spravované aplikace pracuje hostování samotný. Službu zavřete volání <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost>.

Služba je rovněž možné hostovat ve spravované službě Windows, v Internetové informační služby (IIS) nebo ve Windows WAS Process Activation Service (). Další informace o možnosti pro služby hostování najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).

Hostování ve spravované aplikaci služby je nejflexibilnější možností, protože vyžaduje minimálně infrastrukturu pro nasazení. Další informace o hostování služeb ve spravovaných aplikacích najdete v tématu [hostování ve spravované aplikaci](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).

Následující postup ukazuje, jak implementovat v místním prostředí službu v konzolové aplikaci.

## <a name="create-a-self-hosted-service"></a>Vytvoření služby v místním prostředí

1. Vytvořte novou konzolovou aplikaci:

   1. Otevřít Visual Studio a vyberte **nový** > **projektu** z **souboru** nabídky.

   2. V **nainstalované šablony** seznamu vyberte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **Windows Desktop**.

   3. Vyberte **konzolovou aplikaci** šablony. Typ `SelfHost` v **název** pole a klikněte na tlačítko **OK**.

2. Klikněte pravým tlačítkem na **SelfHost** v **Průzkumníka řešení** a vyberte **přidat odkaz**. Vyberte **System.ServiceModel** z **.NET** kartě a klikněte na tlačítko **OK**.

    > [!TIP]
    > Pokud **Průzkumníka řešení** okno není viditelný, vyberte **Průzkumníka řešení** z **zobrazení** nabídky.

3. Dvakrát klikněte na panel **Program.cs** nebo **Module1.vb** v **Průzkumníka řešení** a otevře se v okně kódu, pokud ještě není otevřený. Na začátek souboru přidejte následující příkazy:

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. Definování a implementace kontraktu služby. Tento příklad definuje `HelloWorldService` , který vrací zprávy na základě zadání ke službě.

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > Další informace o tom, jak definovat a implementovat rozhraní služby najdete v tématu [jak: Definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) a [jak: Implementace kontraktu služby](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).

5. V horní části `Main` metody vytvoření instance <xref:System.Uri> třída s atributem základní adresu pro službu.

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy, prochází <xref:System.Type> , které představuje typ služby a základní adresu identifikátoru URI (Uniform Resource) k <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Povolit publikování metadat a následně zavolat <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu <xref:System.ServiceModel.ServiceHost> k inicializaci služby a připravit ji pro příjem zpráv.

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > Tento příklad používá výchozí koncové body a konfigurační soubor je požadovaná pro tuto službu. Pokud jsou nakonfigurované žádné koncové body, modul runtime vytvoří jeden koncový bod pro každou základní adresu pro každou smlouvu službou implementována. Další informace o výchozí koncové body, naleznete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

7. Stisknutím klávesy **Ctrl**+**Shift**+**B** k sestavení řešení.

## <a name="test-the-service"></a>Testování služby

1. Stisknutím klávesy **Ctrl**+**F5** ke spuštění služby.

2. Otevřít **testovací klient WCF**.

    > [!TIP]
    > Chcete-li otevřít **testovací klient WCF**, otevřete příkazový řádek pro vývojáře pro sadu Visual Studio a spusťte **WcfTestClient.exe**.

3. Vyberte **přidat službu** z **souboru** nabídky.

4. Typ `http://localhost:8080/hello` do pole adresy a klikněte na tlačítko **OK**.

    > [!TIP]
    > Ujistěte se, že je služba spuštěná, jinak se tento krok nezdaří. Pokud jste změnili základní adresa v kódu, použijte upravené základní adresy v tomto kroku.

5. Dvakrát klikněte na panel **SayHello** pod **Moje projekty služeb** uzlu. Zadejte svoje jméno do **hodnotu** sloupec **požádat o** seznamu a klikněte na tlačítko **Invoke**.

   Zobrazí se zpráva s odpovědí v **odpovědi** seznamu.

## <a name="example"></a>Příklad

Následující příklad vytvoří <xref:System.ServiceModel.ServiceHost> objekt hostitele služby typu `HelloWorldService`a pak zavolá <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu na <xref:System.ServiceModel.ServiceHost>. Základní adresa jsou uvedené v kódu, je povoleno publikování metadat a používají výchozí koncové body.

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>Viz také:

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [Postupy: Hostování služby WCF v IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)
- [Služby hostování](../../../docs/framework/wcf/hosting-services.md)
- [Postupy: Definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [Postupy: Implementace kontraktu služby](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [Nástroj metadat modelu služby (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Vazby poskytované systémem](../../../docs/framework/wcf/system-provided-bindings.md)
