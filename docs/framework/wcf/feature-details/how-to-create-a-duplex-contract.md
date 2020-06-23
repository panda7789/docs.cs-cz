---
title: 'Postupy: Vytvoření duplexního kontraktu'
description: Naučte se, jak vytvořit duplexní smlouvu, která umožňuje klientům a serverům WCF vzájemně komunikovat nezávisle na sobě. Může buď iniciovat volání do druhé.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: 9320e5b36b8faba3602fbe1df1b95c05dcc7fa7e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247088"
---
# <a name="how-to-create-a-duplex-contract"></a>Postupy: Vytvoření duplexního kontraktu
V tomto tématu se dozvíte o základních krocích pro vytváření metod, které používají oboustranný (obousměrný) kontrakt. Oboustranný kontrakt umožňuje klientům a serverům vzájemně komunikovat nezávisle na sobě, takže může iniciovat volání do druhé. Duplexní smlouva je jedním ze tří vzorů zpráv, které jsou k dispozici pro Windows Communication Foundation služby (WCF). Další dva vzory zpráv jsou jednosměrné a vyžadují odpověď. Duplexní kontrakt se skládá z 2 1 kontraktů mezi klientem a serverem a nevyžaduje, aby byla volání metod korelace. Tento druh smlouvy použijte v případě, že se vaše služba musí dotazovat klienta na Další informace nebo explicitně vyvolat události na straně klienta. Další informace o vytváření klientských aplikací pro duplexní smlouvu najdete v tématu [Postup: přístup ke službám pomocí duplexního kontraktu](how-to-access-services-with-a-duplex-contract.md). Pracovní ukázku najdete v ukázce [duplexní](../samples/duplex.md) ukázka.  
  
### <a name="to-create-a-duplex-contract"></a>Postup vytvoření duplexního kontraktu  
  
1. Vytvořte rozhraní, které vytvoří na straně serveru oboustranně duplexní smlouvu.  
  
2. Použijte <xref:System.ServiceModel.ServiceContractAttribute> třídu na rozhraní.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. Deklaruje signatury metody v rozhraní.  
  
4. Použijte <xref:System.ServiceModel.OperationContractAttribute> třídu pro každý podpis metody, který musí být součástí veřejné smlouvy.  
  
5. Vytvořte rozhraní zpětného volání, které definuje sadu operací, které může služba vyvolat na klientovi.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. Deklarujete signatury metod v rozhraní zpětného volání.  
  
7. Použijte <xref:System.ServiceModel.OperationContractAttribute> třídu pro každý podpis metody, který musí být součástí veřejné smlouvy.  
  
8. Propojte dvě rozhraní s meziduplexní smlouvou nastavením <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> vlastnosti v primárním rozhraní na typ rozhraní zpětného volání.  
  
### <a name="to-call-methods-on-the-client"></a>Volání metod na klienta  
  
1. V implementaci primární smlouvy v rámci služby deklarujte proměnnou pro rozhraní zpětného volání.  
  
2. Nastavte proměnnou na odkaz na objekt vrácený <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> metodou <xref:System.ServiceModel.OperationContext> třídy.  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. Volejte metody definované rozhraním zpětného volání.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje duplexní komunikaci. Kontrakt služby obsahuje operace služby pro přesun dopředu a zpět. Smlouva klienta obsahuje operaci služby pro vytváření sestav své pozice.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- Použití <xref:System.ServiceModel.ServiceContractAttribute> atributů a <xref:System.ServiceModel.OperationContractAttribute> umožňuje automatické generování definic servisních smluv v jazyce WSDL (Web Services Description Language).  
  
- K načtení dokumentu WSDL a (volitelného) kódu a konfiguraci pro klienta použijte [Nástroj pro metadata ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .  
  
- Koncové body, které zveřejňují duplexní služby, musí být zabezpečené. Když služba obdrží duplexní zprávu, při zjištění, kam se má odpověď odeslat, vyhledá na pozici v této příchozí zprávě ReplyTo. Pokud kanál není zabezpečený, může nedůvěryhodný klient odeslat škodlivou zprávu s parametrem ReplyTo cílového počítače, což vede k odepření služby cílového počítače. S běžnými zprávami pro odpověď na požadavek se nejedná o problém, protože parametr ReplyTo je ignorován a odpověď je odeslána na kanál, na kterém byla odeslána původní zpráva.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Postupy: Přístup ke službám pomocí duplexního kontraktu](how-to-access-services-with-a-duplex-contract.md)
- [Duplex](../samples/duplex.md)
- [Navrhování a implementace služeb](../designing-and-implementing-services.md)
- [Postupy: Definování kontraktu služby](../how-to-define-a-wcf-service-contract.md)
- [Relace](../samples/session.md)
