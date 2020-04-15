---
title: 'Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 22713aba4f86fe493ba3d16ef09c2a71b6d55fe0
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389787"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET

Chcete-li nakonfigurovat koncový bod služby WCF (Windows Communication Foundation) tak, aby byl interoperabilní s klienty ASP.NET webové služby, použijte <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ vazby pro koncový bod služby.  
  
 Volitelně můžete povolit podporu pro ověřování https a na úrovni přenosu klienta na vazbě. ASP.NET klienti webové služby nepodporují kódování zpráv <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> MTOM, takže vlastnost by <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>měla být ponechána jako výchozí hodnota, která je . ASP.Net klientů webové služby nepodporují službu <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> WS-Security, takže by měla být nastavena na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Chcete-li zpřístupnit metadata služby WCF pro ASP.NET nástroje pro generování proxy serveru webové služby (tj. [nástroj Web Services Description Language Tool (Wsdl.exe),](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100))Nástroj pro zjišťování [webových služeb (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))a funkci **Přidat webový odkaz** v sadě Visual Studio), měli byste vystavit koncový bod metadat HTTP/GET.  
  
## <a name="add-an-endpoint-in-code"></a>Přidání koncového bodu do kódu  
  
1. Vytvoření nové <xref:System.ServiceModel.BasicHttpBinding> instance  
  
2. Volitelně povolit zabezpečení přenosu pro tuto vazbu koncového <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>bodu služby nastavením režimu zabezpečení pro vazbu na . Podrobnosti naleznete v části [Zabezpečení dopravy](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Přidejte nový koncový bod aplikace do hostitele služby pomocí instance vazby, kterou jste právě vytvořili. Podrobnosti o tom, jak přidat koncový bod služby v kódu, naleznete v tématu [Postup: Vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4. Povolte koncový bod metadat HTTP/GET pro vaši službu. Podrobnosti naleznete v [tématu How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="add-an-endpoint-in-a-configuration-file"></a>Přidání koncového bodu do konfiguračního souboru  
  
1. Vytvořte <xref:System.ServiceModel.BasicHttpBinding> novou konfiguraci vazby. Podrobnosti naleznete v tématu [Postup: Zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2. Volitelně povolit zabezpečení přenosu pro tuto konfiguraci vazby koncového bodu služby nastavením režimu zabezpečení pro vazbu na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Podrobnosti naleznete v tématu [Transport Security](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Nakonfigurujte nový koncový bod aplikace pro vaši službu pomocí konfigurace vazby, kterou jste právě vytvořili. Podrobnosti o přidání koncového bodu služby do konfiguračního souboru naleznete v tématu [Postup: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Povolte koncový bod metadat HTTP/GET pro vaši službu. Podrobnosti naleznete v tématu [Postup: Publikování metadat pro službu pomocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázkový kód ukazuje, jak přidat koncový bod WCF, který je kompatibilní s klienty ASP.NET webové služby v kódu a alternativně v konfiguračních souborech.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [Postupy: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [Postupy: Určení vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)
