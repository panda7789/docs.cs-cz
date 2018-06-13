---
title: 'Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: e30403f9c97f31e93c22a9658ffb74d4d02a49ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490640"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Postupy: Konfigurace klienta WCF na vzájemnou spolupráci se službami WSE3.0
Klienti Windows Communication Foundation (WCF) jsou úroveň kompatibilní s 3.0 vylepšení webové služby pro služby rozhraní Microsoft .NET (WSE), když klienti WCF jsou nakonfigurovány pro použití srpen 2004 verzi specifikace WS-Addressing.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>Konfigurace klienta WCF pro spolupráci s WSE 3.0 webové služby  
  
1.  Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření klienta WCF pro WSE 3.0 webovou službu.  
  
     Pro WSE webovou službu je vytvořit třídu klienta WCF.  
  
     Podrobnosti o vytvoření klienta WCF najdete v tématu [postupy: vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Vytvořte třídu, která představuje vazbu, který může komunikovat s WSE 3.0 Web services.  
  
     Následující třídy je součástí [spolupráce s WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) ukázka.  
  
    1.  Vytvořte třídu, která je odvozena od třídy <xref:System.ServiceModel.Channels.Binding>.  
  
         Následující příklad kódu vytvoří třídu s názvem `WseHttpBinding` odvozený z <xref:System.ServiceModel.Channels.Binding> třídy.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Přidáte vlastnosti pro třídu, která zadejte připraveného assertion WSE, jestli odvozené klíče jsou požadovány, jestli zabezpečených relací se používají, zda jsou požadovány potvrzení podpisu a nastavení ochrany zpráv.  
  
         Následující příklad kódu definuje `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` vlastnosti, které určují připraveného assertion WSE, jestli odvozené klíče jsou požadovány, jestli zabezpečených relací se používají, zda jsou požadovány potvrzení podpisu a nastavení ochrany zprávy, v uvedeném pořadí.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Přepsání <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metodu a nastavit vlastnosti vazby.  
  
         Následující příklad kódu určuje přenosu, kódování zpráv a nastavení ochrany zpráv získáním hodnoty `SecurityAssertion` a `MessageProtectionOrder` vlastnosti.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  V kódu aplikace klienta přidáte kód pro nastavení vlastnosti vazby.  
  
     Následující příklad kódu určuje, že klienta WCF musí používat ochranu zprávu a ověřování podle definice WSE 3.0 `AnonymousForCertificate` assertion připraveného zabezpečení. Kromě toho jsou vyžadovány zabezpečených relací a odvozené klíče.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje vlastní vazby, která zveřejňuje vlastnosti, které odpovídají vlastnosti kontrolní výraz WSE 3.0 to zabezpečení. Vlastní vazby, která se nazývá `WseHttpBinding`, se pak použije k určení vlastnosti vazby pro klienta WCF.  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.Binding>  
 [Spolupráce s WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
