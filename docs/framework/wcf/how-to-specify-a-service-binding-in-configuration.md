---
title: 'Postupy: Zadání vazby služby v konfiguraci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 245fe50ed5a80c51163652defb642cebefd55dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184023"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Postupy: Zadání vazby služby v konfiguraci
V tomto příkladu `ICalculator` je smlouva definována pro službu základní `CalculatorService` kalkulačky, služba je implementována ve třídě a její koncový bod je <xref:System.ServiceModel.BasicHttpBinding>nakonfigurován v souboru Web.config, kde je uvedeno, že služba používá . Popis konfigurace této služby pomocí kódu namísto konfigurace naleznete v tématu [How to: Specify a Service Binding in Code](how-to-specify-a-service-binding-in-code.md).  
  
 Obvykle je osvědčeným postupem zadat vazby a adresu informace deklarativně v konfiguraci, nikoli imperativně v kódu. Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy pro nasazenou službu se obvykle liší od těch, které se používají při vývoji služby. Obecněji řečeno, udržování vazby a adresování informace z kódu umožňuje změnit bez nutnosti znovu zkompilovat nebo znovu nasadit aplikaci.  
  
 Pomocí [nástroje Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)lze provedení všech následujících kroků konfigurace.  
  
 Zdrojovou kopii tohoto příkladu naleznete v tématu [BasicBinding](./samples/basicbinding.md).  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Určení funkce BasicHttpBinding, která se má použít ke konfiguraci služby  
  
1. Definujte servisní smlouvu pro typ služby.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. Implementujte servisní smlouvu ve třídě služeb.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > Informace o adrese nebo vazbě nejsou zadány v rámci implementace služby. Kód také nemusí být zapsán, aby se tyto informace načítají z konfiguračního souboru.  
  
3. Vytvořte soubor Web.config pro konfiguraci `CalculatorService` koncového <xref:System.ServiceModel.WSHttpBinding>bodu, který používá soubor .  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  

            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint
                address=""
                binding="wsHttpBinding"  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. Vytvořte soubor Service.svc, který obsahuje následující řádek, a umístěte jej do virtuálního adresáře Internetové informační služby (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a>Změna výchozích hodnot vlastností vazby  
  
1. Chcete-li upravit jednu z <xref:System.ServiceModel.WSHttpBinding>výchozích hodnot vlastností `<binding name="Binding1">` , vytvořte nový název konfigurace vazby - - v rámci elementu [ \<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) a nastavte nové hodnoty pro atributy vazby v tomto elementu vazby. Chcete-li například změnit výchozí hodnoty časového limitu otevření a zavření 1 minuty až 2 minuty, přidejte do konfiguračního souboru následující.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Viz také

- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
- [Zadání adresy koncového bodu](specifying-an-endpoint-address.md)
