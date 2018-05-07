---
title: 'Postupy: Vytvoření základní webové služby HTTP WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: d147286fd2f8fe3f4f5e822598a07b51ae6d9791
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Postupy: Vytvoření základní webové služby HTTP WCF
Windows Communication Foundation (WCF) umožňuje vytvoření který zveřejňuje koncový bod webové služby. Koncových bodů webové odesílat data XML nebo JSON, že neexistují žádné obálku protokolu SOAP. Toto téma ukazuje, jak vystavit takové koncový bod.  
  
> [!NOTE]
>  Jediný způsob, jak zabezpečit koncový bod webové je zveřejnění prostřednictvím protokolu HTTPS, pomocí zabezpečení přenosu. Při použití zabezpečení na základě zpráv, informace o zabezpečení je obvykle umístěny v hlavičkách protokolu SOAP a protože zprávy odeslané do koncových bodů protokolu SOAP obsahovat žádné obálku protokolu SOAP, není nikde umístit informace o zabezpečení a musíte spoléhat na zabezpečení přenosu.  
  
### <a name="to-create-a-web-endpoint"></a>Chcete-li vytvořit koncový bod webové  
  
1.  Definování kontraktu služby pomocí rozhraní označené jako <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> a <xref:System.ServiceModel.Web.WebGetAttribute> atributy.  
  
     [!code-csharp[htBasicService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]  
  
    > [!NOTE]
    >  Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje POST volání operace. Můžete však zadat metodu protokolu HTTP (například HEAD, PUT nebo odstraňte) pro mapování na operaci zadáním "metoda =" parametr. <xref:System.ServiceModel.Web.WebGetAttribute> nemá "metoda =" parametr a pouze mapy GET volání operace služby.  
  
2.  Implementujte kontrakt služby.  
  
     [!code-csharp[htBasicService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]  
  
### <a name="to-host-the-service"></a>K hostování služby  
  
1.  Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu.  
  
     [!code-csharp[htBasicService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]  
  
2.  Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
     [!code-csharp[htBasicService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]  
  
    > [!NOTE]
    >  Pokud je nemůžete přidat koncový bod, <xref:System.ServiceModel.Web.WebServiceHost> automaticky vytvoří výchozí koncový bod. <xref:System.ServiceModel.Web.WebServiceHost> také přidá <xref:System.ServiceModel.Description.WebHttpBehavior> a zakáže stránku nápovědy HTTP a funkci GET webové služby popis Language (WSDL), takže koncový bod metadat nebudou v konfliktu s výchozí koncový bod HTTP.  
    >   
    >  Přidání koncový bod-protokolu SOAP s adresou URL služby "" způsobí neočekávanému chování, když je proveden pokus o volání operace v koncovém bodě. Důvodem je naslouchání, identifikátor URI koncového bodu je stejný jako identifikátor URI pro stránku nápovědy (stránka, která se zobrazí, když přejdete na základní adresa služby WCF).  
  
     Můžete provést jednu z následujících akcí k tomu nedocházelo:  
  
    -   Vždycky zadejte prázdný identifikátor URI pro koncový bod-protokolu SOAP.  
  
    -   Vypněte na stránce nápovědy. To lze provést následujícím kódem.  
  
     [!code-csharp[htBasicService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]  
  
3.  Otevření hostitele služby a počkejte, dokud uživatel stiskne klávesu ENTER.  
  
     [!code-csharp[htBasicService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]  
  
     Tento příklad ukazuje, jak hostování stylu webové služby pomocí konzolové aplikace. Můžete taky hostitele služby v rámci služby IIS. Chcete-li to provést, zadejte <xref:System.ServiceModel.Activation.WebServiceHostFactory> třídy v souboru .svc, jak ukazuje následující kód.  
  
    ```  
          <%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Samples.Service"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory%>  
    ```  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>K volání operací služby namapované na GET v Internet Exploreru  
  
1.  Otevřete Internet Explorer a zadejte "`http://localhost:8000/EchoWithGet?s=Hello, world!`" a stiskněte klávesu ENTER. Adresa URL obsahuje základní adresa služby ("http://localhost:8000/"), relativní adresa koncového bodu (""), operace služby k volání ("EchoWithGet") a otazník následuje seznam pojmenované parametry oddělených ampersandem (&).  
  
### <a name="to-call-service-operations-in-code"></a>K volání operací služby v kódu  
  
1.  Vytvoření instance <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` v rámci `using` bloku.  
  
     [!code-csharp[htBasicService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]  
  
2.  Přidat <xref:System.ServiceModel.Description.WebHttpBehavior> ke koncovému bodu <xref:System.ServiceModel.ChannelFactory> volání.  
  
     [!code-csharp[htBasicService#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]  
  
3.  Vytvoření kanálu a volání služby.  
  
     [!code-csharp[htBasicService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]  
  
4.  Zavřít <xref:System.ServiceModel.Web.WebServiceHost>.  
  
     [!code-csharp[htBasicService#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]  
  
## <a name="example"></a>Příklad  
 Zde je úplný výpis pro tento příklad kódu.  
  
 [!code-csharp[htBasicService#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
 [!code-vb[htBasicService#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilování Service.cs odkaz System.ServiceModel.dll a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
