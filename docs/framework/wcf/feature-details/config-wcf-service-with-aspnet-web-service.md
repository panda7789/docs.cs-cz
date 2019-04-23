---
title: 'Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 84762d8917609b84a049ea665b575acfa6e5fecf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325186"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET
Konfigurace koncového bodu služby Windows Communication Foundation (WCF), aby vzájemná spolupráce s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby klientů, použijte <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ vazby pro vaše koncové body služby.  
  
 Volitelně můžete povolit podporu protokolu HTTPS a ověřování klientů na úrovni přenosu na vazbu. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Klienty webové služby nepodporují kódování MTOM zpráv, takže <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> vlastnost ponechte výchozí hodnotu, která je <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. Klienti webové služby ASP.Net nepodporují WS-Security, takže <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> by mělo být nastavené <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Aby metadata pro služby WCF k dispozici [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové nástroje pro generování proxy služby (to znamená [Web Services Description Language Tool (Wsdl.exe)](https://go.microsoft.com/fwlink/?LinkId=73833), [nástroj zjišťování webové služby (Disco.exe)](https://go.microsoft.com/fwlink/?LinkId=73834)a přidat webový odkaz funkce v sadě Visual Studio), je potřeba zveřejnit koncový bod metadat HTTP/GET.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>K přidání koncového bodu WCF, který je kompatibilní s klienty webové služby ASP.NET v kódu  
  
1. Vytvořte nový <xref:System.ServiceModel.BasicHttpBinding> instance  
  
2. Volitelně můžete povolit zabezpečení přenosu pro tuto vazbu koncového bodu služby pomocí nastavení režimu zabezpečení rozhraní pro vytvoření vazby na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Podrobnosti najdete v tématu [zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Přidáte nový koncový bod aplikace na hostitele služby pomocí vazby instanci, kterou jste právě vytvořili. Podrobnosti o tom, jak přidat koncový bod služby v kódu, najdete v článku [jak: Vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4. Povolení koncového bodu HTTP/GET metadat pro vaši službu. Podrobnosti najdete v tématu [jak: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>K přidání koncového bodu WCF, který je kompatibilní s klienty webové služby ASP.NET v konfiguračním souboru  
  
1. Vytvořte nový <xref:System.ServiceModel.BasicHttpBinding> konfigurace vazby. Podrobnosti najdete v tématu [jak: Zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2. Volitelně můžete povolit zabezpečení přenosu pro tuto konfiguraci vazby koncového bodu služby pomocí nastavení režimu zabezpečení rozhraní pro vytvoření vazby na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Podrobnosti najdete v tématu [zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Konfigurace nového koncového bodu aplikace pro vaši službu pomocí konfigurace vazby, který jste právě vytvořili. Podrobnosti o tom, jak přidat koncový bod služby v konfiguračním souboru, najdete v článku [jak: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Povolení koncového bodu HTTP/GET metadat pro vaši službu. Podrobnosti najdete v tématu [jak: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat koncový bod WCF, který je kompatibilní s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webových klientů služby v kódu a také v konfiguračních souborech.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [Postupy: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [Postupy: Zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)
