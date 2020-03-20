---
title: 'Postupy: Načítání metadat a implementace kompatibilní služby'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 0a13d504b1c7c38ec13fee58c36913a75119271b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184864"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Postupy: Načítání metadat a implementace kompatibilní služby
Často, stejná osoba není navrhovat a implementovat služby. V prostředích, kde jsou důležité interoperační aplikace, mohou být smlouvy navrženy nebo popsány v jazyce WSDL (Web Services Description Language) a vývojář musí implementovat službu, která je v souladu s poskytnutou smlouvou. Můžete také chtít migrovat existující službu do Windows Communication Foundation (WCF), ale zachovat formát drátu. Kromě toho duplexní smlouvy vyžadují volající implementovat kontrakt zpětného volání také.  
  
 V těchto případech je nutné použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (nebo ekvivalentní nástroj) generovat rozhraní servisní smlouvy ve spravovaném jazyce, který můžete implementovat ke splnění požadavků smlouvy. Nástroj [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) se obvykle používá k získání smlouvy o poskytování služeb, která se používá s objektem factory kanálu nebo typu klienta WCF, stejně jako s konfiguračním souborem klienta, který nastavuje správnou vazbu a adresu. Chcete-li použít generovaný konfigurační soubor, musíte jej změnit na konfigurační soubor služby. Může být také nutné upravit servisní smlouvu.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Načtení dat a implementace kompatibilní služby  
  
1. Nástroj [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proti souborům metadat nebo koncovému bodu metadat vygenerujte soubor kódu.  
  
2. Vyhledejte část výstupního souboru kódu, která obsahuje rozhraní zájmu (v případě, že <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> existuje více než jeden), který je označen atributem. Následující příklad kódu ukazuje dvě rozhraní generovaná [nástrojem ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) První (`ISampleService`) je rozhraní servisní smlouvy, které implementujete k vytvoření kompatibilní služby. Druhý (`ISampleServiceChannel`) je pomocné rozhraní pro použití klienta, <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> který rozšiřuje rozhraní smlouvy o poskytování služeb a je pro použití v klientské aplikaci.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. Pokud WSDL neurčuje akci odpovědi pro všechny operace, generované operace smlouvy <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> může mít vlastnost nastavena na zástupný znak (*). Odeberte toto nastavení vlastnosti. V opačném případě při implementaci metadat smlouvy o poskytování služeb metadata nelze exportovat pro tyto operace.  
  
4. Implementujte rozhraní ve třídě a hostujte službu. Příklad najdete v [tématu How to: Implement a Service Contract](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), nebo viz jednoduchá implementace níže v příkladu části.  
  
5. V konfiguračním souboru klienta, který generuje [nástroj ServiceModel Metadata Utility Tool (Svcutil.exe),](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) změňte oddíl [ \<konfigurace>klienta](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) na oddíl služby>konfigurace. (Příklad generovaného konfiguračního souboru klientské aplikace naleznete v následující části Příklad.)  
  
6. V části [ \<Služby>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) `name` konfigurace vytvořte atribut v části [ \<služby>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) konfigurace pro implementaci služby.  
  
7. Nastavte atribut `name` služby na název konfigurace pro implementaci služby.  
  
8. Přidejte prvky konfigurace koncového bodu, které používají implementovanou servisní smlouvu, do části konfigurace služby.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje většinu souboru kódu generovaného spuštěním [nástroje ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proti souborům metadat.  
  
 Následující kód ukazuje:  
  
- Rozhraní servisní smlouvy, které při implementaci splňuje požadavky`ISampleService`smlouvy ( ).  
  
- Pomocné rozhraní pro použití klienta, které rozšiřuje <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> rozhraní smlouvy o poskytování`ISampleServiceChannel`služeb a je pro použití v klientské aplikaci ( ).  
  
- Pomocná třída, která <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> rozšiřuje a je pro`SampleServiceClient`použití v klientské aplikaci ( ).  
  
- Konfigurační soubor generovaný ze služby.  
  
- Jednoduchá `ISampleService` implementace služby.  
  
- Převod konfiguračního souboru na straně klienta na verzi na straně služby.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]
  
## <a name="see-also"></a>Viz také

- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
