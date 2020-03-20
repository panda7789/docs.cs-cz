---
title: 'Postupy: Zadání klientské vazby v konfiguraci'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 574f56173c2acfcf41a5e9a9e99abe45281e3636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184041"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Postupy: Zadání klientské vazby v konfiguraci
V tomto příkladu je vytvořena aplikace klientské konzole pro použití služby kalkulačky a vazba pro tohoto klienta je zadána deklarativně v konfiguraci. Klient přistupuje k `CalculatorService` `ICalculator` aplikaci , která implementuje <xref:System.ServiceModel.BasicHttpBinding> rozhraní, a služba i klient používají třídu.  
  
 Uvedený postup předpokládá, že je spuštěna služba kalkulačky. Informace o tom, jak vytvořit službu, naleznete v [tématu How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md). Používá také [ServiceModel Metadata Utility Tool (Svcutil.exe),](servicemodel-metadata-utility-tool-svcutil-exe.md) který poskytuje Windows Communication Foundation (WCF) automaticky generovat klientské součásti. Nástroj generuje klientský kód a konfiguraci pro přístup ke službě.  
  
 Klient je postaven ve dvou částech. Svcutil.exe `ClientCalculator` generuje, který implementuje `ICalculator` rozhraní. Tato klientská aplikace je pak vytvořena `ClientCalculator`vytvořením instance aplikace .  
  
 Obvykle je osvědčeným postupem zadat vazby a adresu informace deklarativně v konfiguraci, nikoli imperativně v kódu. Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy pro nasazenou službu se obvykle liší od těch, které se používají při vývoji služby. Obecněji řečeno, udržování vazby a adresování informace z kódu umožňuje změnit bez nutnosti znovu zkompilovat nebo znovu nasadit aplikaci.  
  
 Pomocí [nástroje Editor configuration Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)můžete provést všechny následující kroky konfigurace .  
  
 Zdrojovou kopii tohoto příkladu naleznete v ukázce [BasicBinding.](./samples/basicbinding.md)  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Určení vazby klienta v konfiguraci  
  
1. Pomocí příkazu Svcutil.exe z příkazového řádku vygenerujte kód z metadat služby.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Klient, který je generován `ICalculator` obsahuje rozhraní, které definuje servisní smlouvy, které implementace klienta musí splňovat.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. Vygenerovaný klient také `ClientCalculator`obsahuje implementaci .  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Svcutil.exe také generuje konfiguraci pro klienta, který používá třídu. <xref:System.ServiceModel.BasicHttpBinding> Při použití sady Visual Studio pojmenujte tento soubor App.config. Všimněte si, že adresa a informace o vazbě nejsou zadány nikde v rámci implementace služby. Kód také nemusí být zapsán, aby bylo možné načíst tyto informace z konfiguračního souboru.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. Vytvořte instanci `ClientCalculator` v aplikaci a potom zavolejte operace služby.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. Zkompilujte a spusťte klienta.  
  
## <a name="see-also"></a>Viz také

- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
