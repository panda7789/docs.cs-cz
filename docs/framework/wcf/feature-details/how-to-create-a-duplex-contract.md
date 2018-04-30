---
title: 'Postupy: Vytvoření duplexního kontraktu'
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
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c06bd4f050eda3c3374684b5401b8c85fb9e1df9
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-duplex-contract"></a>Postupy: Vytvoření duplexního kontraktu
Toto téma ukazuje základní kroky pro vytvoření metody, které používají duplexního kontraktu (obousměrné). Duplexní kontrakt umožňuje klienty a servery pro komunikaci mezi sebou nezávisle tak, aby buď můžete spustit volání na druhý. Duplexní kontrakt je jedním ze tří vzorů zprávy k dispozici pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby. Další dva zprávy vzory jsou jednosměrná a požadavku a odpovědi. Duplexního kontraktu se skládá ze dvou jednosměrné kontrakty mezi klientem a serverem a nevyžaduje korelaci volání metody. Tento druh kontrakt použijte, pokud vaše služba musí dotazovat klienta pro další informace nebo explicitně vyvolávání událostí na klientovi. Další informace o vytváření klientskou aplikaci pro duplexního kontraktu najdete v tématu [postupy: přístup k službám pomocí duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Ukázku práce, najdete [duplexní](../../../../docs/framework/wcf/samples/duplex.md) ukázka.  
  
### <a name="to-create-a-duplex-contract"></a>K vytvoření duplexního kontraktu  
  
1.  Vytvořte rozhraní, které tvoří duplexního kontraktu na straně serveru.  
  
2.  Použít <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3.  Podpisy metoda v rozhraní deklarujte.  
  
4.  Použít <xref:System.ServiceModel.OperationContractAttribute> třída pro každý podpis metody, které musí být součástí veřejného kontraktu.  
  
5.  Vytvořte rozhraní zpětného volání, která definuje sadu operací, které můžete vyvolat službu na straně klienta.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6.  Deklarujte podpisy metoda v rozhraní zpětného volání.  
  
7.  Použít <xref:System.ServiceModel.OperationContractAttribute> třída pro každý podpis metody, které musí být součástí veřejného kontraktu.  
  
8.  Propojení dvě rozhraní do duplexního kontraktu nastavením <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> vlastnost v primární rozhraní pro typ rozhraní zpětného volání.  
  
### <a name="to-call-methods-on-the-client"></a>Volání metody na straně klienta  
  
1.  V implementaci služby primární kontraktu deklarujte proměnnou pro rozhraní zpětného volání.  
  
2.  Nastavte proměnnou na odkaz na objekt vrácený <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> metodu <xref:System.ServiceModel.OperationContext> třídy.  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3.  Volání metody definované rozhraní zpětného volání.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje duplexní komunikace. Kontrakt služby obsahuje operací služby pro přesun vpřed a zpět. Kontrakt klienta obsahuje operace služby pro vytváření sestav jeho umístění.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   Použití <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributy umožňuje automatické generování definice kontraktu služby ve webové služby popis Language (WSDL).  
  
-   Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k načtení dokumentu WSDL a kódu (volitelné) a konfigurace pro klienta.  
  
-   Koncové body vystavení duplexní služby musí být zabezpečená. Když služba přijme zprávu o duplexní, vypadá to na ReplyTo v této příchozí zprávy k určení místa k odeslání odpovědi. Pokud není zabezpečený kanál, může nedůvěryhodného klienta odeslat škodlivý zprávu s ReplyTo cílový počítač vedoucí k odmítnutí služby cílového počítače. S regulární požadavku a odpovědi zprávy to není problém, protože ReplyTo je ignorován a odpovědi se odesílají na kanál, který původní zpráva byla přijata v na.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Postupy: Přístup ke službám pomocí duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Duplex](../../../../docs/framework/wcf/samples/duplex.md)  
 [Navrhování a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Postupy: Definování kontraktu služby](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Relace](../../../../docs/framework/wcf/samples/session.md)
