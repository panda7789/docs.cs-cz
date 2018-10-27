---
title: 'Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 5cbe982049d1df6e2c714ca0b63de0db7577452e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187306"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0
Klientů Windows Communication Foundation (WCF) jsou přenosový kompatibilní s Web Services vylepšení 3.0 služby rozhraní Microsoft .NET (Najít), když klienti WCF umožňují použít verzi specifikace WS-Addressing ze srpna 2004.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>Konfigurace klienta WCF pro spolupráci s WSE 3.0 webové služby  
  
1.  Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření klienta WCF pro WSE 3.0 webovou službu.  
  
     WSE webové služby je vytvořená třída klienta WCF.  
  
     Podrobnosti o vytvoření klienta WCF najdete v tématu [postupy: vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Vytvořte třídu, která představuje vazbu, která může komunikovat s WSE 3.0 Web services.  
  
     Následující třídy je součástí [spolupráce s WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) vzorku.  
  
    1.  Vytvořte třídu, která je odvozena od třídy <xref:System.ServiceModel.Channels.Binding>.  
  
         Následující příklad kódu vytvoří třídu s názvem `WseHttpBinding` , který je odvozen od <xref:System.ServiceModel.Channels.Binding> třídy.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Přidání vlastností do třídy, která zadejte výraz na klíč WSE, určuje, zda jsou požadovány odvozené klíče, určuje, zda se používají zabezpečené relace, určuje, zda jsou požadovány nacházejí potvrzení podpisů a nastavení ochrany zprávy.  
  
         Následující příklad kódu definuje `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` vlastnosti, které určují kontrolního výrazu WSE na klíč, určuje, zda jsou požadovány odvozené klíče, určuje, zda se používají zabezpečené relace, určuje, zda jsou požadovány nacházejí potvrzení podpisů a nastavení ochrany zprávy v uvedeném pořadí.  
  
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
 Následující příklad kódu definuje vlastní vazby, které zpřístupní vlastnosti, které odpovídají vlastnosti kontrolní výraz WSE 3.0 na klíč zabezpečení. Vlastní vazby, který se nazývá `WseHttpBinding`, se pak použije k určení vlastností vazby pro klienta WCF.  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.Binding>  
 [Spolupráce s WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)