---
title: 'Postupy: Vytvoření duplexního kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: 8cc53f6842d55892ae178e22e2835555a132778b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693633"
---
# <a name="how-to-create-a-duplex-contract"></a>Postupy: Vytvoření duplexního kontraktu
Toto téma popisuje základní kroky k vytvoření metody, které používají duplexního kontraktu (obousměrné). Duplexní kontrakt umožňuje klientům a serverům komunikovat mezi sebou nezávisle tak, aby buď inicializaci volání do jiné. Duplexní kontrakt je jedním ze tří vzorů zprávy k dispozici pro služby Windows Communication Foundation (WCF). Další dvě zprávy vzory jsou jednosměrná a požadavek odpověď. Duplexní kontrakt se skládá ze dvou jednosměrné kontrakty mezi klientem a serverem a nevyžaduje korelaci volání metody. Tento typ kontraktu použijte, pokud vaše služba musí dotazování klienta pro další informace nebo explicitně vyvolat události na straně klienta. Další informace o vytváření klientské aplikace pro duplexní kontrakt, naleznete v tématu [jak: Přístup ke službám pomocí duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Pracovní ukázku najdete v tématu [duplexní](../../../../docs/framework/wcf/samples/duplex.md) vzorku.  
  
### <a name="to-create-a-duplex-contract"></a>K vytvoření duplexního kontraktu  
  
1.  Vytvoření rozhraní, které tvoří duplexního kontraktu na straně serveru.  
  
2.  Použít <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3.  Deklarujte podpisy metod v rozhraní.  
  
4.  Použít <xref:System.ServiceModel.OperationContractAttribute> třídy pro každý podpis metody, které musí být součástí veřejného kontraktu.  
  
5.  Vytvoření rozhraní zpětného volání, která definuje sadu operací, které můžete vyvolat službu na straně klienta.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6.  Deklarujte podpisy metod rozhraní zpětného volání.  
  
7.  Použít <xref:System.ServiceModel.OperationContractAttribute> třídy pro každý podpis metody, které musí být součástí veřejného kontraktu.  
  
8.  Propojit dvě rozhraní do duplexního kontraktu tak, že nastavíte <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> vlastnost v primární rozhraní pro typ rozhraní zpětného volání.  
  
### <a name="to-call-methods-on-the-client"></a>Volání metody na straně klienta  
  
1.  V implementaci služby z primární smlouvy deklarujte proměnnou pro rozhraní zpětného volání.  
  
2.  Nastavte proměnnou na odkaz na objekt, který je vrácený <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> metodu <xref:System.ServiceModel.OperationContext> třídy.  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3.  Volání metody definované rozhraní zpětného volání.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje duplexní komunikaci. Kontrakt služby obsahuje operace služby pro přesun vpřed a zpět. Kontrakt klienta obsahuje operace služby pro vytváření sestav jeho pozice.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   Použití <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributy umožňuje automatické generování definice kontraktu služby ve na webové služby WSDL (Description Language).  
  
-   Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k načtení dokumentu WSDL a (volitelně) kódu a konfigurace pro klienta.  
  
-   Koncové body vystavení duplexní služby musí být zabezpečená. Služba přijme zprávu duplexní, dohlíží na ReplyTo v této příchozí zprávy k určení, kam chcete odeslat odpověď. Pokud není zabezpečený kanál, může nedůvěryhodného klienta odeslat škodlivý zprávu s ReplyTo cílový počítač, což vede k odepření služby cílového počítače. Zprávy regulární požadavek odpověď to není problém, protože ReplyTo je ignorována a odpověď je odeslána na kanál, který byl původní zprávu v na.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Postupy: Přístup ke službám pomocí duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Duplex](../../../../docs/framework/wcf/samples/duplex.md)
- [Navrhování a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Postupy: Definování kontraktu služby](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [Relace](../../../../docs/framework/wcf/samples/session.md)
