---
title: 'Postupy: Hostování služby WCF v IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 580b380a6c6349c6a4efa26e3eefe38bd660fa1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184925"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Postupy: Hostování služby WCF v IIS
Toto téma popisuje základní kroky potřebné k vytvoření služby WCF (Windows Communication Foundation), která je hostována v Internetové informační službě (IIS). Toto téma předpokládá, že jste se známe se sestáleji se sestálecí mise a rozumíte tomu, jak pomocí nástroje pro správu iis vytvářet a spravovat aplikace iis. Další informace o službě IIS naleznete v [tématu Internetová informační služba](https://www.iis.net/). Služba WCF spuštěná v prostředí služby IIS plně využívá výhod funkcí služby IIS, jako je recyklace procesů, nečinné vypnutí, monitorování stavu procesů a aktivace založená na zprávách. Tato možnost hostování vyžaduje, aby byla služba IIS správně nakonfigurována, ale nevyžaduje, aby byl jako součást aplikace zapsán žádný kód pro hostování. Službu IIS můžete používat pouze s přenosem HTTP.  
  
 Další informace o interakci wcf a ASP.NET naleznete v tématu [WCF Services a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). Další informace o konfiguraci zabezpečení naleznete v [tématu Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Zdrojovou kopii tohoto příkladu naleznete v tématu [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Vytvoření služby hostované službou IIS  
  
1. Zkontrolujte, zda je v počítači nainstalována a spuštěna i ii. Další informace o instalaci a konfiguraci služby IIS naleznete v [tématu Instalace a konfigurace služby IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)  
  
2. Vytvořte novou složku pro soubory aplikace s názvem "IISHostedCalcService", ujistěte se, že ASP.NET má přístup k obsahu složky a pomocí nástroje pro správu služby IIS vytvořte novou aplikaci služby IIS, která je fyzicky umístěna v tomto adresáři aplikace. Při vytváření aliasu pro adresář aplikace použijte "IISHostedCalc".  
  
3. Vytvořte nový soubor s názvem service.svc v adresáři aplikace. Upravte tento soubor @ServiceHost přidáním následujícího prvku.  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. Vytvořte App_Code podadresář v adresáři aplikace.  
  
5. Vytvořte kódový soubor s názvem Service.cs v podadresáři App_Code.  
  
6. Přidejte následující příkazy pomocí do horní části souboru Service.cs.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. Za příkazy using přidejte následující deklaraci oboru názvů.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. Definujte servisní smlouvu uvnitř deklarace oboru názvů, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Implementujte servisní smlouvu po definici servisní smlouvy, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Vytvořte soubor s názvem "Web.config" v adresáři aplikace a přidejte do něj následující konfigurační kód. Za běhu wcf infrastruktury používá informace k vytvoření koncového bodu, který klientské aplikace mohou komunikovat.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     Tento příklad explicitně určuje koncové body v konfiguračním souboru. Pokud do služby nepřidáte žádné koncové body, runtime přidá výchozí koncové body za vás. Další informace o výchozích koncových bodech, vazbách a chováních naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Chcete-li se ujistit, že je služba hostována správně, otevřete instanci aplikace Internet Explorer a přejděte na adresu URL služby:`http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Příklad  
 Následuje úplný seznam kódu služby Kalkulačka hostovaná službou IIS.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Viz také

- [Hostování v Internetové informační službě](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Služby hostování](../../../../docs/framework/wcf/hosting-services.md)
- [Služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
- [Funkce hostování prostředků pro aplikace systému Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
