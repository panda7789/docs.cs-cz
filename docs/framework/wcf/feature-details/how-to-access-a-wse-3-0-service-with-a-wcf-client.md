---
title: 'Postupy: Přístup ke službě WSE 3.0 pomocí klienta WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 54d795858b85bd72a01f619b3603c9927df655d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492522"
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Postupy: Přístup ke službě WSE 3.0 pomocí klienta WCF
Klienti Windows Communication Foundation (WCF) jsou úroveň kompatibilní s Web Services vylepšení (WSE) 3.0 pro služby rozhraní Microsoft .NET, když klienti WCF jsou nakonfigurovány pro použití srpen 2004 verzi specifikace WS-Addressing. Však služby WSE 3.0 nepodporuje protokol exchange (MEX) metadata, tak při použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pro vytvoření třídy klienta WCF, nastavení zabezpečení se nepoužijí pro generovaný objekt Klienta WCF. Proto je třeba zadat nastavení zabezpečení, WSE 3.0 služba vyžaduje, aby po vygenerování klienta WCF.  
  
 Tato nastavení zabezpečení můžete použít s využitím vlastní vazby vzít v úvahu službě WSE 3.0 požadavky a požadavky na umožňuje vzájemnou spolupráci mezi službou WSE 3.0 a klienta WCF. Tyto požadavky na interoperabilitu zahrnují zmíněnými použití v srpnu 2004 specifikaci WS-Addressing a WSE 3.0default zprávy ochranu <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. Je výchozí ochrana zpráva pro WCF <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Toto téma podrobné informace o tom, jak vytvořit vazbu WCF, které spolupracuje se službou WSE 3.0. WCF taky poskytuje ukázku, která zahrnuje tuto vazbu. Další informace o této ukázky najdete v tématu [spolupráce s webovými službami ASMX](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Pro přístup ke službě WSE 3.0 Web pomocí klienta WCF  
  
1.  Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření klienta WCF pro WSE 3.0 webovou službu.  
  
     Pro WSE 3.0 webové služby bude vytvořena klienta WCF. Protože WSE 3.0 nepodporuje protokol MEX, nelze použít nástroj načíst požadavky na zabezpečení pro webovou službu. Vývojář aplikace musíte přidat nastavení zabezpečení pro klienta.  
  
     Další informace o vytvoření klienta WCF najdete v tématu [postupy: vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Vytvořte třídu, která představuje vazbu, který může komunikovat s WSE 3.0 Web services.  
  
     Následující třídy je součástí [spolupráce s WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) ukázka:  
  
    1.  Vytvořte třídu, která je odvozena od třídy <xref:System.ServiceModel.Channels.Binding>.  
  
         Následující příklad kódu vytvoří třídu s názvem `WseHttpBinding` odvozený z <xref:System.ServiceModel.Channels.Binding> třídy.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Přidáte vlastnosti pro třídu, která zadejte připraveného assertion WSE používá službu WSE, jestli odvozené klíče jsou požadovány, jestli zabezpečených relací se používají, zda jsou požadovány potvrzení podpisu a nastavení ochrany zpráv. Ve WSE 3.0 to assertion určuje požadavky na zabezpečení pro klienta nebo webové službě – podobná režim ověřování pro vazbu v WCF.  
  
         Následující příklad kódu definuje `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, a `MessageProtectionOrder` vlastnosti, které určují připraveného assertion WSE, zda odvozené klíče jsou požadovány, zda zabezpečených relací se používají, jestli podpis potvrzení jsou povinné a nastavení ochrany zprávy, v uvedeném pořadí.  
  
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
 Následující příklad kódu definuje vlastní vazby, která zveřejňuje vlastnosti, které odpovídají vlastnosti kontrolní výraz WSE 3.0 to zabezpečení. Vlastní vazbou, který se nazývá `WseHttpBinding`, pak slouží k určení vlastnosti vazby pro klienta WCF, který komunikuje s ukázkou WSSecurityAnonymous WSE 3.0 rychlý start.  
  
  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.Binding>  
 [Spolupráce s WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
