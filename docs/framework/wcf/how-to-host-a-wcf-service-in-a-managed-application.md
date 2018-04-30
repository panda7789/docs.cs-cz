---
title: 'Postupy: Hostování služby WCF ve spravované aplikaci'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: 42
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f2671dc381e0d3ef8f55ced01268de6205fcb7d
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a>Postupy: Hostování služby WCF ve spravované aplikaci
K hostování služby ve spravované aplikaci, vkládat kód pro službu uvnitř kódu spravované aplikace, definujte koncový bod služby buď imperativní v kódu deklarativně prostřednictvím konfigurace, nebo pomocí výchozí koncové body a pak vytvořte instance <xref:System.ServiceModel.ServiceHost>.  
  
 Chcete-li začít přijímat zprávy, volejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>. Tím se vytvoří a otevře naslouchací proces pro danou službu. Hostitelská služba tímto způsobem se často označuje jako "vlastní hostování" protože spravované aplikace provádí hostování práce sám sebe. Službu zavřete volání <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost>.  
  
 Služba může být hostovaný také ve spravované službě Windows, v Internetové informační služby (IIS) nebo v procesu aktivace služby WAS (Windows). Další informace o hostování možnosti pro služby najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
 Hostování ve spravované aplikaci služby je nejvíce flexibilní možnost, protože vyžaduje minimálně infrastrukturu pro nasazování. Další informace o hostování služeb ve spravovaných aplikacích najdete v tématu [hostování ve spravované aplikaci](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).  
  
 Následující postup ukazuje, jak implementovat samoobslužné hostovanou službu v konzolové aplikaci.  
  
### <a name="to-create-a-self-hosted-service"></a>Chcete-li vytvořit služba s vlastním hostováním  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] a vyberte **nový**, **projektu...**  z **souboru** nabídky.  
  
2.  V **nainstalovaných šablonách** seznamu, vyberte **Visual C#**, **Windows** nebo **jazyka Visual Basic**, **Windows**. V závislosti na vaší [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] nastavení, jednu nebo obě tyto může být v rámci **jiné jazyky** uzel v **nainstalovaných šablonách** seznamu.  
  
3.  Vyberte **konzolové aplikace** z **Windows** seznamu. Typ `SelfHost` v **název** pole a klikněte na tlačítko **OK**.  
  
4.  Klikněte pravým tlačítkem na **SelfHost** v **Průzkumníku řešení** a vyberte **přidat odkaz na...** . Vyberte **System.ServiceModel** z **.NET** a klikněte na **OK**.  
  
    > [!TIP]
    >  Pokud **Průzkumníku řešení** okno není viditelná, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.  
  
5.  Klikněte dvakrát na **Program.cs** nebo **Module1.vb** v **Průzkumníku řešení** a otevře se v okně kód, pokud ještě není otevřené. V horní části souboru přidejte následující příkazy.  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  Definování a implementace kontraktu služby. Tento příklad definuje `HelloWorldService` , vrátí se mu zpráva, na základě zadání ke službě.  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  Další informace o tom, jak definovat a implementovat rozhraní služby najdete v tématu [postupy: definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) a [postupy: implementace kontraktu služby](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).  
  
7.  V horní části `Main` metody vytvoření instance <xref:System.Uri> se základní adresa pro službu.  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy a předejte <xref:System.Type> této představuje typ služby a základní adres identifikátor URI (Uniform Resource) k <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Povolit publikování metadat a pak zavolají <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu <xref:System.ServiceModel.ServiceHost> k inicializaci služby a příprava přijímat zprávy.  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  Tento příklad používá výchozí koncové body a žádný konfigurační soubor je vyžadovaný pro tuto službu. Pokud jsou nakonfigurované žádné koncové body, modul runtime vytvoří jeden koncový bod pro každou základní adresu pro každý kontrakt služby implementované službu. Další informace o výchozí koncové body najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
### <a name="to-test-the-service"></a>K testování služby  
  
1.  Stiskněte kombinaci kláves Ctrl + F5 ke spouštění služby.  
  
2.  Otevřete **testovacího klienta WCF**.  
  
    > [!TIP]
    >  Chcete-li otevřít **testovacího klienta WCF**, otevřete [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] příkazový řádek a spusťte **WcfTestClient.exe**.  
  
3.  Vyberte **přidat službu...**  z **souboru** nabídky.  
  
4.  Typ `http://localhost:8080/hello` do pole Adresa a klikněte na tlačítko **OK**.  
  
    > [!TIP]
    >  Ujistěte se, že je služba spuštěná, jinak tento krok nezdaří. Pokud jste změnili základní adresa ve kód, pomocí upravené základní adresy v tomto kroku.  
  
5.  Klikněte dvakrát na **SayHello** pod **Moje projekty služeb** uzlu. Zadejte název do **hodnotu** sloupec v **požadavku** seznamu a klikněte na tlačítko **Invoke**. Zobrazí se zpráva odpovědi v **odpovědi** seznamu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.ServiceModel.ServiceHost> objektu k hostování služby typu `HelloWorldService`a potom zavolá <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu <xref:System.ServiceModel.ServiceHost>. Základní adresa je uvedené v kódu, je povoleno publikování metadat a používají výchozí koncové body.  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [Postupy: Hostování služby WCF v IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)  
 [Služby hostování](../../../docs/framework/wcf/hosting-services.md)  
 [Postupy: Definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Postupy: Implementace kontraktu služby](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Vazby poskytované systémem](../../../docs/framework/wcf/system-provided-bindings.md)
