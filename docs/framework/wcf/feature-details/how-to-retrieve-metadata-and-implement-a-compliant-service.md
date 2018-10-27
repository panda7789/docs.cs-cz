---
title: 'Postupy: načítání metadat a implementace kompatibilní služby'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: dc7f5d97a5201698e8dc99e4523e3ab2925f6883
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185219"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Postupy: načítání metadat a implementace kompatibilní služby
Stejné osobě často není navrhování a implementaci služby. V prostředích, kde jsou důležitá spolupráce aplikací smlouvy můžete určená nebo je popsáno v webové služby WSDL (Description Language) a vývojář musí implementovat službu, která splňuje zadaný kontraktu. Můžete také migrovat existující službu pro Windows Communication Foundation (WCF), ale zachovat přenosový formát. Kromě toho duplexní kontrakty vyžadovat volající implementovat kontrakt zpětného volání.  
  
 V těchto případech je nutné použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (nebo ekvivalentní nástroje) ke generování rozhraní kontraktu služby v spravovaného jazyka, který může implementovat ke splnění požadavků kontrakt. Obvykle [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) slouží k získání kontraktu služby, který se používá objekt pro vytváření kanálů nebo typ klienta WCF, můžou mít konfigurační soubor klienta, který nastaví správnou vazbu a adresu. Použití generovaných konfiguračních souborů, musíte jej změnit v konfiguračním souboru služby. Také budete muset upravit kontrakt služby.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Načtení dat a implementace kompatibilní služby  
  
1.  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proti soubory metadat nebo koncový bod metadat pro generování souboru kódu.  
  
2.  Vyhledejte část výstupního souboru kódu, který obsahuje rozhraní, které vás zajímají (v případě existuje více než jeden), která je označena pomocí <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atribut. Následující příklad kódu ukazuje dvě rozhraní generovaných [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). První (`ISampleService`) je rozhraní kontraktu služby, které můžete implementovat pro vytvoření kompatibilní služby. Druhý (`ISampleServiceChannel`) je pomocná rozhraní pro použití klienta, který rozšiřuje oba rozhraní servisní smlouvy a <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> a je určen pro použití v klientské aplikaci.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  Pokud rozhraní jazyka WSDL neurčuje akci odpovědi pro všechny operace, kontrakty generované operace může mít <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> nastavenou na zástupný znak (*). Odeberte nastavení této vlastnosti. V opačném případě při implementaci kontraktu metadata služby nelze exportovat metadata pro tyto operace.  
  
4.  Toto rozhraní implementovat třídy a hostitelem služby. Příklad najdete v tématu [postupy: implementace kontraktu služby](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), nebo se podívejte na jednoduché implementace níže v části příklad.  
  
5.  V konfiguraci klienta souboru, který [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje, změnit [ \<klienta >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) konfiguračního oddílu pro [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) konfigurační oddíl. (Příklad konfiguračního souboru generovaného klienta aplikace najdete v části "Vzorový".)  
  
6.  V rámci [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) konfigurace části, vytvořte `name` atribut [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) konfiguračního oddílu pro vaši službu implementace.  
  
7.  Nastavení služby `name` atribut názvu konfigurace pro implementaci služby.  
  
8.  Přidáte prvky konfigurace koncového bodu, které používají implementované servisní smlouvy ke konfiguračnímu oddílu služby.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje většinou generován spuštěním souboru kódu [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proti soubory metadat.  
  
 Následující kód ukazuje:  
  
-   Kontrakt služby rozhraní, pokud je implementována, v souladu s požadavky smlouvy (`ISampleService`).  
  
-   Rozhraní pomocné rutiny pro použití klienta, který rozšiřuje oba rozhraní servisní smlouvy a <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> a je určen pro použití v klientské aplikaci (`ISampleServiceChannel`).  
  
-   Pomocná třída, která rozšiřuje <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> a je určen pro použití v klientské aplikaci (`SampleServiceClient`).  
  
-   Konfigurační soubor, který je generován ze služby.  
  
-   Jednoduchý `ISampleService` implementaci služby.  
  
-   Převod na straně klienta konfigurační soubor na straně služby verzi.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a>Viz také  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
