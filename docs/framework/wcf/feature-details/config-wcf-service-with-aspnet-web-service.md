---
title: 'Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 7e07e8d8781040d4ddc1d5643446f5a42354a557
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963552"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET
Chcete-li nakonfigurovat koncový bod služby Windows Communication Foundation (WCF) pro spolupráci s klienty webové služby ASP.NET, použijte jako typ vazby pro koncový bod služby typ <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>.  
  
 Volitelně můžete povolit podporu ověřování klientů pomocí protokolu HTTPS a na úrovni přenosu na vazbu. Klienti webové služby ASP.NET nepodporují kódování zpráv MTOM, takže vlastnost <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> by měla být ponechána jako výchozí hodnota, která je <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. Klienti webové služby ASP.Net nepodporují WS-Security, takže <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> by měly být nastavené na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Aby byla k dispozici metadata služby WCF pro ASP.NET nástroje pro generování proxy webových služeb (tj. [Nástroj Web Services Description Language Tool (WSDL. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100)), [Nástroj pro zjišťování webových služeb (Disc. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))a funkce Přidat webový odkaz v aplikaci Visual Studio), měli byste zveřejnit koncový bod metadat HTTP/GET.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>Přidání koncového bodu WCF, který je kompatibilní s klienty webové služby ASP.NET v kódu  
  
1. Vytvoří novou instanci <xref:System.ServiceModel.BasicHttpBinding>.  
  
2. Volitelně můžete povolit zabezpečení přenosu pro tuto vazbu koncového bodu služby nastavením režimu zabezpečení pro vazbu na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Podrobnosti najdete v tématu [Security Transport](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Pomocí instance vazby, kterou jste právě vytvořili, přidejte do hostitele služby nového koncového bodu aplikace. Podrobnosti o tom, jak přidat koncový bod služby v kódu, naleznete v tématu [Postupy: Vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4. Povolte pro vaši službu koncový bod metadat HTTP/GET. Podrobnosti najdete v tématu [Postupy: publikování metadat pro službu pomocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Přidání koncového bodu WCF, který je kompatibilní s klienty webové služby ASP.NET v konfiguračním souboru  
  
1. Vytvoří novou konfiguraci vazby <xref:System.ServiceModel.BasicHttpBinding>. Podrobnosti najdete v tématu [Postupy: určení vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2. Volitelně můžete povolit zabezpečení přenosu pro tuto konfiguraci vazby koncového bodu služby nastavením režimu zabezpečení pro vazbu na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Podrobnosti najdete v tématu [zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Nakonfigurujte nový koncový bod aplikace pro vaši službu pomocí konfigurace vazby, kterou jste právě vytvořili. Podrobnosti o tom, jak přidat koncový bod služby do konfiguračního souboru, najdete v tématu [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Povolte pro vaši službu koncový bod metadat HTTP/GET. Podrobnosti najdete v tématu [Postupy: publikování metadat pro službu pomocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat koncový bod WCF, který je kompatibilní s klienty webové služby ASP.NET v kódu a případně v konfiguračních souborech.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [Postupy: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [Postupy: Určení vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)
