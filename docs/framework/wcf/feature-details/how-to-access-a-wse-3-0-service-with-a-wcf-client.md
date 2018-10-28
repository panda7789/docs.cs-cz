---
title: 'Postupy: Přístup ke službě WSE 3.0 pomocí klienta WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 3de4bb4546d3ee20e961ecf5a9d130e8e6c713a8
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193809"
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Postupy: Přístup ke službě WSE 3.0 pomocí klienta WCF
Klienti Windows Communication Foundation (WCF) jsou přenosový kompatibilní s Web Services vylepšení (WSE) 3.0 pro služby rozhraní Microsoft .NET, když klienti WCF umožňují použít verzi ze srpna 2004 specifikace WS-Addressing. Ale WSE 3.0 services nepodporuje metadata exchange (MEX) protokol, tak při použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pro vytvoření třídy klienta WCF, se nepoužijí nastavení zabezpečení pro generované Klient WCF. Proto je nutné zadat nastavení zabezpečení, že WSE 3.0 služba vyžaduje, aby po vygenerování klienta WCF.  
  
 Vezměte v úvahu požadavky službě WSE 3.0 a interoperabilní požadavky mezi službou WSE 3.0 a klienta WCF pomocí vlastní vazby můžete použít nastavení zabezpečení. Tyto požadavky na interoperabilitu zahrnují výše uvedené použití ze srpna 2004 specifikace WS-Addressing a WSE 3.0default zprávy ochranu <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. Je výchozí ochrana zprávy WCF <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Toto téma podrobně popisuje, jak vytvořit vazby WCF, která spolupracuje se službou WSE 3.0. WCF obsahuje také ukázky, která zahrnuje tuto vazbu. Další informace o této ukázce najdete v tématu [spolupráce s webovými službami ASMX](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Přístup ke službě WSE 3.0 Web pomocí klienta WCF  
  
1.  Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření klienta WCF pro WSE 3.0 webovou službu.  
  
     WSE 3.0 webové služby vytvoří se klient WCF. Protože WSE 3.0 nepodporuje protokol MEX, nemůžete použít nástroj načíst požadavky na zabezpečení pro webovou službu. Vývojář aplikace musíte přidat nastavení zabezpečení pro klienta.  
  
     Další informace o vytvoření klienta WCF najdete v tématu [postupy: vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Vytvořte třídu, která představuje vazbu, která může komunikovat s WSE 3.0 Web services.  
  
     Následující třídy je součástí [spolupráce s WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) vzorku:  
  
    1.  Vytvořte třídu, která je odvozena od třídy <xref:System.ServiceModel.Channels.Binding>.  
  
         Následující příklad kódu vytvoří třídu s názvem `WseHttpBinding` , který je odvozen od <xref:System.ServiceModel.Channels.Binding> třídy.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Přidání vlastnosti do třídy, zadáte na klíč kontrolní výraz WSE používané službě WSE, určuje, zda jsou požadovány odvozené klíče, určuje, zda se používají zabezpečené relace, určuje, zda jsou požadovány nacházejí potvrzení podpisů a nastavení ochrany zprávy. Ve službě WSE 3.0 na klíč tvrzení určuje požadavky na zabezpečení pro klientské nebo webové službě – podobně jako režim ověřování vazby ve službě WCF.  
  
         Následující příklad kódu definuje `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, a `MessageProtectionOrder` vlastnosti, které určují kompletních kontrolního výrazu WSE, zda odvozené klíče jsou požadovány, zda se používají zabezpečené relace, ať už podpis potvrzení jsou povinné a nastavení ochrany zprávy, v uvedeném pořadí.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Přepsat <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metody nastavte vlastnosti vazby.  
  
         Následující příklad kódu určuje přenos, kódování zpráv a nastavení ochrany zpráv hodnoty s informacemi `SecurityAssertion` a `MessageProtectionOrder` vlastnosti.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  V kódu aplikace klienta přidejte kód pro nastavení vlastnosti vazby.  
  
     Následující příklad kódu určuje, zda klient WCF musí používat zprávy ochrany a ověřování podle definice ve WSE 3.0 `AnonymousForCertificate` kontrolního výrazu zabezpečení na klíč. Navíc se vyžaduje zabezpečených relací a odvozených klíčů.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje vlastní vazby, které zpřístupní vlastnosti, které odpovídají vlastnosti kontrolní výraz WSE 3.0 na klíč zabezpečení. Tento vlastní vazby, který se nazývá `WseHttpBinding`, se pak použije k určení vlastností vazby pro klienta WCF, který komunikuje s ukázkou WSSecurityAnonymous WSE 3.0 rychlý start.  
  
  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.Binding>  
 [Spolupráce s WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
