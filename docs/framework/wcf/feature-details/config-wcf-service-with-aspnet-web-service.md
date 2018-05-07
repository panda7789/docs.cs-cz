---
title: 'Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 12c5645b53e8e931edabc1a13fc1749e40538044
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET
Ke konfiguraci koncového bodu služby Windows Communication Foundation (WCF) jako vzájemná spolupráce s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby klientů, použijte <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ vazby pro svůj koncový bod služby.  
  
 Volitelně můžete umožnit podporu pro protokol HTTPS a ověření klienta transportní vrstvy na vazby. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Webové služby klienti nepodporují kódování MTOM zpráva, proto <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> vlastnost by měla být ponecháno jeho výchozí hodnotu, která je <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. Klienti webové služby ASP.Net nepodporují WS-zabezpečení, proto <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> musí být nastavena na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Pro zpřístupnění metadata pro služby WCF pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové nástroje pro generování proxy služby (to znamená, [Web Services Description Language Tool (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833), [webové služby zjišťování nástroj (Disco.exe)](http://go.microsoft.com/fwlink/?LinkId=73834)a přidat webový odkaz funkce v sadě Visual Studio), by měl vystavit koncový bod HTTP nebo získat metadata.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>Chcete-li přidat koncový bod WCF, který je kompatibilní s klienty webové služby ASP.NET v kódu  
  
1.  Vytvořte novou <xref:System.ServiceModel.BasicHttpBinding> instance  
  
2.  Volitelně můžete povolit zabezpečení přenosu pro tuto vazbu koncového bodu služby podle nastavení režimu zabezpečení rozhraní vazby <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Podrobnosti najdete v tématu [zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Přidejte nový koncový bod aplikace do vaší hostitele služby pomocí vazby instance, kterou jste právě vytvořili. Podrobnosti o tom, jak přidat koncový bod služby v kódu najdete v tématu [postupy: vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4.  Povolení koncového bodu protokolu HTTP nebo získat metadata pro vaši službu. Podrobnosti najdete v tématu [postupy: publikování metadat služby pomocí kód](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Chcete-li přidat koncový bod WCF, který je kompatibilní s klienty webové služby ASP.NET v konfiguračním souboru  
  
1.  Vytvořte novou <xref:System.ServiceModel.BasicHttpBinding> Konfigurace vazeb. Podrobnosti najdete v tématu [postupy: zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2.  Volitelně můžete povolit zabezpečení přenosu pro tuto konfiguraci vazby koncového bodu služby podle nastavení režimu zabezpečení rozhraní vazby <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Podrobnosti najdete v tématu [zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Konfigurace nového koncového bodu aplikace služby pomocí vazby konfigurace, kterou jste právě vytvořili. Podrobnosti o tom, jak přidat koncový bod služby v konfiguračním souboru najdete v tématu [postupy: vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4.  Povolení koncového bodu protokolu HTTP nebo získat metadata pro vaši službu. Podrobnosti najdete v tématu [postupy: publikování metadat služby promocí konfigurační soubor](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat koncový bod WCF, který je kompatibilní s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webových služeb klientům v kódu a případně v konfiguračních souborech.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 [Postupy: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 [Postupy: Určení vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)
