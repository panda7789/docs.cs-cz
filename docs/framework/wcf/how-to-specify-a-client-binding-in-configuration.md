---
title: 'Postupy: Zadání klientské vazby v konfiguraci'
description: Naučte se, jak zadat vazbu pro klienta WCF deklarativně v konfiguračním souboru. V tomto příkladu přistupuje klient ke službě.
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 28778b6ae853199c5d7943f329bb087760f4bb11
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244488"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Postupy: Zadání klientské vazby v konfiguraci
V tomto příkladu je aplikace konzoly klienta vytvořena pro použití služby kalkulačky a vazba pro tohoto klienta je v konfiguraci určena deklarativně. Klient přistupuje k `CalculatorService` rozhraní, které implementuje `ICalculator` rozhraní a jak službu, tak i klient používající <xref:System.ServiceModel.BasicHttpBinding> třídu.  
  
 Tento postup předpokládá, že je spuštěná služba kalkulačky. Informace o tom, jak vytvořit službu, naleznete v tématu [How to: zadat vazbu služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md). Používá také nástroj pro dodávání [metadat (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , který Windows Communication Foundation (WCF) poskytuje k automatickému generování komponent klienta. Nástroj vygeneruje kód klienta a konfiguraci pro přístup ke službě.  
  
 Klient je sestaven ve dvou částech. Svcutil.exe generuje `ClientCalculator` rozhraní, které implementuje `ICalculator` rozhraní. Tato klientská aplikace je pak vytvořena konstrukcí instance `ClientCalculator` .  
  
 Obvykle je osvědčeným postupem zadat vazby a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu. Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby. Obecně platí, že zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace.  
  
 Pomocí [nástroje Editor konfigurací (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)můžete provádět všechny následující konfigurační kroky.  
  
 Zdrojovou kopii tohoto příkladu najdete v ukázce [BasicBinding](./samples/basicbinding.md) .  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Určení vazby klienta v konfiguraci  
  
1. K vygenerování kódu z metadat služby použijte Svcutil.exe z příkazového řádku.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Vygenerovaný klient obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí implementace klienta splňovat.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. Vygenerovaný klient také obsahuje implementaci `ClientCalculator` .  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Svcutil.exe také generuje konfiguraci pro klienta, který používá <xref:System.ServiceModel.BasicHttpBinding> třídu. Při použití sady Visual Studio pojmenujte tento soubor App.config. Všimněte si, že informace o adrese a vazbě nejsou zadány kamkoli v rámci implementace služby. Také není nutné zapisovat kód pro načtení těchto informací z konfiguračního souboru.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. Vytvořte instanci `ClientCalculator` v aplikaci a potom zavolejte operace služby.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. Zkompilujte a spusťte klienta.  
  
## <a name="see-also"></a>Viz také

- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
