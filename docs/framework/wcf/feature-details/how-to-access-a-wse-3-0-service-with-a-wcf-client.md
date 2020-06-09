---
title: 'Postupy: Přístup ke službě WSE 3.0 pomocí klienta WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 179591c272685771fbde12e161cb38b1bd969052
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597199"
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Postupy: Přístup ke službě WSE 3.0 pomocí klienta WCF
Klienti Windows Communication Foundation (WCF) jsou kompatibilní s rozšířeními webových služeb (WSE) 3,0 pro služby Microsoft .NET, když jsou klienti WCF nakonfigurovaní tak, aby používali specifikaci WS-Addressing ve verzi ze srpna 2004. Služby WSE 3,0 ale nepodporují protokol MEX (Metadata Exchange), takže pokud k vytvoření třídy klienta WCF použijete nástroj pro tvorbu [metadat (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , nastavení zabezpečení se nepoužijí pro vygenerovaného klienta WCF. Proto je nutné zadat nastavení zabezpečení, která služba WSE 3,0 vyžaduje po vygenerování klienta služby WCF.  
  
 Tato nastavení zabezpečení můžete uplatnit pomocí vlastní vazby, která bude brát v úvahu požadavky služby WSE 3,0 a interoperabilní požadavky mezi službou WSE 3,0 a klientem WCF. Tyto požadavky na interoperabilitu zahrnují výše uvedené použití specifikace WS-Addressing ze srpna 2004 a výchozí ochranu zpráv WSE 3.0 <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> . Výchozí ochrana zpráv pro WCF je <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> . Toto téma podrobně popisuje, jak vytvořit vazbu WCF, která spolupracuje se službou WSE 3,0. WCF také poskytuje ukázku, která zahrnuje tuto vazbu. Další informace o této ukázce najdete v tématu [spolupráce s webovými službami ASMX](../samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Přístup k webové službě WSE 3,0 pomocí klienta WCF  
  
1. Spusťte [Nástroj Svcutil. exe](../servicemodel-metadata-utility-tool-svcutil-exe.md) pro vytváření klienta WCF pro webovou službu WSE 3,0.  
  
     Pro webovou službu WSE 3,0 se vytvoří klient WCF. Vzhledem k tomu, že WSE 3,0 nepodporuje protokol MEX, nemůžete použít nástroj k načtení požadavků zabezpečení pro webovou službu. Vývojář aplikace musí přidat nastavení zabezpečení pro klienta.  
  
     Další informace o vytváření klienta WCF naleznete v tématu [Postupy: Vytvoření klienta](../how-to-create-a-wcf-client.md).  
  
2. Vytvořte třídu, která představuje vazbu, která může komunikovat s webovými službami WSE 3,0.  
  
     Následující třída je součástí [spolupracujícího s WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) Sample:  
  
    1. Vytvořte třídu, která je odvozena od třídy <xref:System.ServiceModel.Channels.Binding>.  
  
         Následující příklad kódu vytvoří třídu s názvem `WseHttpBinding` , která je odvozena z <xref:System.ServiceModel.Channels.Binding> třídy.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. Přidejte do třídy vlastnosti, které určují kontrolní výraz WSE klíč používaný službou WSE, zda jsou povinné odvozené klíče, zda jsou používány zabezpečené relace, zda jsou vyžadovány potvrzení podpisů a nastavení ochrany zpráv. V WSE 3,0 kontrolní výraz klíč určuje požadavky na zabezpečení pro klienta nebo webovou službu, podobně jako režim ověřování vazby ve službě WCF.  
  
         Následující příklad kódu definuje `SecurityAssertion` `RequireDerivedKeys` vlastnosti,, `EstablishSecurityContext` a `MessageProtectionOrder` , které určují kontrolní výraz WSE klíč, zda jsou povinné odvozené klíče, zda jsou používány zabezpečené relace, zda jsou vyžadovány potvrzení podpisů a nastavení ochrany zpráv v uvedeném pořadí.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. Přepsat <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metodu pro nastavení vlastností vazby.  
  
         Následující příklad kódu určuje přenos, kódování zpráv a nastavení ochrany zpráv pomocí získání hodnot `SecurityAssertion` `MessageProtectionOrder` vlastností a.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. V kódu klientské aplikace přidejte kód pro nastavení vlastností vazby.  
  
     Následující příklad kódu určuje, že klient služby WCF musí používat ochranu zpráv a ověřování podle definice `AnonymousForCertificate` kontrolního výrazu zabezpečení WSE 3,0 klíč. Navíc se vyžadují zabezpečené relace a odvozené klíče.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje vlastní vazbu, která zveřejňuje vlastnosti, které odpovídají vlastnostem kontrolního výrazu zabezpečení WSE 3,0 klíč. Tato vlastní vazba, která je pojmenována `WseHttpBinding` , se pak používá k určení vlastností vazby pro klienta WCF, který komunikuje s ukázkou WSSECURITYANONYMOUS WSE 3,0 Starting.  

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Channels.Binding>
- [Spolupráce s WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
