---
title: 'Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 7dd50fcc07c6c090042cf87acb4aa5d2b5321a68
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579576"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0
Klienti služby Windows Communication Foundation (WCF) jsou kompatibilní s vylepšeními webových služeb 3,0 pro služby Microsoft .NET (WSE), když jsou klienti WCF nakonfigurováni na použití verze specifikace WS-Addressing ze srpna 2004.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>Konfigurace klienta WCF pro spolupráci s webovou službou WSE 3,0  
  
1. Spusťte [Nástroj Svcutil. exe](../servicemodel-metadata-utility-tool-svcutil-exe.md) pro vytváření klienta WCF pro webovou službu WSE 3,0.  
  
     Pro webovou službu WSE se vytvoří Třída klienta WCF.  
  
     Podrobnosti o vytvoření klienta WCF naleznete v tématu [Postupy: Vytvoření klienta](../how-to-create-a-wcf-client.md).  
  
2. Vytvořte třídu, která představuje vazbu, která může komunikovat s webovými službami WSE 3,0.  
  
     Následující třída je součástí [spolupracujícího s WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) Sample.  
  
    1. Vytvořte třídu, která je odvozena od třídy <xref:System.ServiceModel.Channels.Binding>.  
  
         Následující příklad kódu vytvoří třídu s názvem `WseHttpBinding` , která je odvozena z <xref:System.ServiceModel.Channels.Binding> třídy.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. Přidejte do třídy vlastnosti, které určují kontrolní výraz WSE klíč, zda jsou povinné odvozené klíče, zda jsou používány zabezpečené relace, zda jsou vyžadovány potvrzení podpisů a nastavení ochrany zpráv.  
  
         Následující příklad kódu definuje `SecurityAssertion` `RequireDerivedKeys` vlastnosti,, a `EstablishSecurityContext` `MessageProtectionOrder` . Určují kontrolní výraz WSE klíč, zda jsou povinné odvozené klíče, zda jsou používány zabezpečené relace, zda jsou vyžadovány potvrzení podpisů a nastavení ochrany zpráv v uvedeném pořadí.  
  
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
 Následující příklad kódu definuje vlastní vazbu, která zveřejňuje vlastnosti, které odpovídají vlastnostem kontrolního výrazu zabezpečení WSE 3,0 klíč. Vlastní vazba, která je pojmenována `WseHttpBinding` , se pak použije k určení vlastností vazby pro klienta WCF.  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Channels.Binding>
- [Spolupráce s WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
