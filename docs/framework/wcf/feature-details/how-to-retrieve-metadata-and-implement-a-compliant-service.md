---
title: 'Postupy: Načítání metadat a implementace kompatibilní služby'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 6bd67ec8dcc0e73d097796b44974dce00b9a4eb2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601215"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Postupy: Načítání metadat a implementace kompatibilní služby
Stejná osoba často nenavrhuje a neimplementuje služby. V prostředích, kde jsou mezi operačními aplikacemi důležité, je možné smlouvy navrhovat nebo popsány v jazyce WSDL (Web Services Description Language) a vývojář musí implementovat službu, která je v souladu se zadaným kontraktem. Je také možné, že budete chtít migrovat existující službu na Windows Communication Foundation (WCF), ale zachovat formát komunikace. Duplexní kontrakty navíc vyžadují, aby volající implementovali taky kontrakt zpětného volání.  
  
 V těchto případech musíte použít nástroj pro doplňování [metadat (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) (nebo ekvivalentní nástroj) k vygenerování rozhraní kontraktu služby ve spravovaném jazyce, který můžete implementovat pro splnění požadavků smlouvy. Nástroj pro dodávání [metadat (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) se obvykle používá k získání kontraktu služby, který se používá s objektem pro vytváření kanálů, nebo s typem klienta WCF a také s konfiguračním souborem klienta, který nastavuje správnou vazbu a adresu. Chcete-li použít generovaný konfigurační soubor, je nutné jej změnit na konfigurační soubor služby. Je také možné, že budete muset kontrakt služby upravit.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Načtení dat a implementace kompatibilní služby  
  
1. K vygenerování souboru s kódem použijte [Nástroj Svcutil. exe (ServiceModel Metadata Utility)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pro soubory metadat nebo koncový bod metadat.  
  
2. Vyhledejte část souboru s výstupním kódem, která obsahuje rozhraní zájmu (v případě, že existuje více než jedna), která je označena <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atributem. Následující příklad kódu ukazuje dvě rozhraní generovaná [nástrojem ServiceModel Metadata Utility (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). První ( `ISampleService` ) je rozhraní kontraktu služby, které implementujete k vytvoření vyhovující služby. Druhá ( `ISampleServiceChannel` ) je pomocné rozhraní pro klientské použití, které rozšiřuje rozhraní kontraktu služby a <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> je používáno v klientské aplikaci.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. Pokud WSDL neurčuje akci odpovědi pro všechny operace, vygenerované kontrakty operace mohou mít <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> vlastnost nastavenou na zástupný znak (*). Odeberte nastavení této vlastnosti. V opačném případě při implementaci metadat kontraktu služby nejde metadata pro tyto operace exportovat.  
  
4. Implementujte rozhraní ve třídě a hostovat službu. Příklad naleznete v tématu [How to: Implement a Service kontrakt](../how-to-implement-a-wcf-contract.md)nebo v části příklad se podívejte na jednoduchou implementaci.  
  
5. V konfiguračním souboru klienta, který nástroj pro dodávání [metadat ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) vygeneruje, změňte [\<client>](../../configure-apps/file-schema/wcf/client.md) konfigurační oddíl na [\<services>](../../configure-apps/file-schema/wcf/services.md) konfigurační oddíl. (Příklad vygenerovaného konfiguračního souboru klientské aplikace naleznete v následující části "Příklad".)  
  
6. V [\<services>](../../configure-apps/file-schema/wcf/services.md) části Configuration (konfigurace) vytvořte `name` v [\<services>](../../configure-apps/file-schema/wcf/services.md) části konfigurace pro vaši implementaci služby atribut.  
  
7. Nastavte atribut Service `name` na název konfigurace pro vaši implementaci služby.  
  
8. Přidejte prvky konfigurace koncového bodu, které používají implementovaný kontrakt služby, do konfiguračního oddílu služby.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje většinu souboru kódu generovaného spuštěním [nástroje Svcutil. exe (Nástroj pro metadata ServiceModel)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pro soubory metadat.  
  
 Následující kód ukazuje:  
  
- Rozhraní kontraktu služby, které při implementaci splňuje požadavky kontraktu ( `ISampleService` ).  
  
- Pomocné rozhraní pro použití klientem, které rozšiřuje rozhraní kontraktu služby a <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> je používáno v klientské aplikaci ( `ISampleServiceChannel` ).  
  
- Pomocná třída, která rozšiřuje <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> a je určena pro použití v klientské aplikaci ( `SampleServiceClient` ).  
  
- Konfigurační soubor vygenerovaný službou.  
  
- Jednoduchá `ISampleService` implementace služby.  
  
- Převod konfiguračního souboru na straně klienta na verzi služby.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]
  
## <a name="see-also"></a>Viz také

- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
