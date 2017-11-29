---
title: "Postupy: načtení metadat a implementovat kompatibilní služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: adb1cb9006c6f0e01008dd5f610c4c340c7ddbff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Postupy: načtení metadat a implementovat kompatibilní služby
Často stejná osoba není návrh a implementaci služby. V prostředích, kde jsou důležité spolupráce aplikace kontrakty lze určený nebo popsané v webové služby popis Language (WSDL) a vývojář musí implementovat služba, která odpovídá zadané kontrakt. Můžete také migrovat existující službu pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ale zachovat přenosový formát. Duplexní kontrakty navíc vyžadují volající implementace kontraktu zpětného volání.  
  
 V těchto případech je nutné použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (nebo ekvivalentní nástroje) ke generování rozhraní kontraktu služby ve spravovaných jazyk, který můžete implementovat ke splnění požadavků kontrakt. Obvykle [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) se používá k získání kontraktu služby, který se používá v kanálu nebo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i stejně jako u klienta konfiguračního souboru, který nastaví typ klienta správné vazby a adresu. Použijte vygenerovaný konfigurační soubor, je nutné změnit ji do konfiguračního souboru služby. Můžete také upravit kontrakt služby.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Načtení dat a implementovat kompatibilní služby  
  
1.  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proti soubory metadat nebo koncový bod metadat pro generování kódu souboru.  
  
2.  Vyhledejte část výstupní kód soubor, který obsahuje rozhraní zájmu (v případě je více než jeden) označené <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atribut. Následující příklad kódu ukazuje dvě rozhraní generované [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). První (`ISampleService`) je rozhraní kontraktu služby, které můžete implementovat pro vytvoření služby kompatibilní. Druhý (`ISampleServiceChannel`) je rozhraní pomocné rutiny pro použití klienta, který rozšiřuje obě rozhraní služby kontraktu a <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> a je určen pro použití v aplikaci klienta.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  Pokud schématu WSDL neurčuje akci odpovědi pro všechny operace, mohou obsahovat kontrakty generovaného operaci <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> vlastnost nastavena na hodnotu zástupného znaku (*). Odeberte nastavení této vlastnosti. Jinak při implementaci kontraktu metadata služby nelze exportovat metadata pro tyto operace.  
  
4.  Toto rozhraní implementovat na třídě a hostitelem služby. Příklad, naleznete v části [postupy: implementace kontraktu služby](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), nebo v tématu jednoduché implementace níže v části příklad.  
  
5.  V konfiguraci klienta souboru, který [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje, změnit [ \<klienta >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) konfigurační oddíl [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) konfigurační oddíl. (Příklad konfiguračního souboru aplikace generovaného klienta, najdete v části "Příklad".)  
  
6.  V rámci [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) konfigurace, vytvořte `name` atribut [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) konfigurační oddíl pro služby implementace.  
  
7.  Nastavení služby `name` atribut názvu konfigurace týkající se vaší implementace služby.  
  
8.  Přidejte konfigurační prvky koncový bod, které používají kontrakt služby implementované v sekci konfigurace služby.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje většinu kódu soubor generovaný spuštěním [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proti soubory metadat.  
  
 Následující kód ukazuje:  
  
-   Kontrakt služby rozhraní, pokud je implementována, v souladu s požadavky kontrakt (`ISampleService`).  
  
-   Pomocná rozhraní pro použití klienta, který rozšiřuje obě rozhraní služby kontraktu a <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> a je určen pro použití v aplikaci klienta (`ISampleServiceChannel`).  
  
-   Pomocná třída, která rozšiřuje <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> a je určen pro použití v aplikaci klienta (`SampleServiceClient`).  
  
-   Konfigurační soubor generované ze služby.  
  
-   Jednoduchý `ISampleService` implementace služby.  
  
-   Převod souboru konfigurace na straně klienta na straně služby verzi.  
  
 [!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]    
 [!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     
 [!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    
 [!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a>Viz také  
 [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
