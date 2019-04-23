---
title: 'Postupy: Určení vazby služby v konfiguraci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 911c13b2a24c1906fe3da787460209f12296c993
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337120"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Postupy: Určení vazby služby v konfiguraci
V tomto příkladu `ICalculator` smlouvy je definován pro službu základní kalkulačky, služba se implementuje v `CalculatorService` třídě a následně svůj koncový bod je nakonfigurovaný v souboru Web.config, kde je zadán, že služba používá <xref:System.ServiceModel.BasicHttpBinding> . Popis konfigurace této služby promocí kódu místo konfigurace najdete v tématu [jak: Zadání vazby služby v kódu](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).  
  
 Obvykle je osvědčeným postupem určete vazbu a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu. Definování koncových bodů v kódu není obvykle praktické protože vazeb a adresy pro službu nasazenou se obvykle liší od nastavení použít, je vyvíjena služby. Obecně platí udržování vazby a adresování informace mimo kód jim umožňuje změnit bez nutnosti znovu kompilovat nebo znovu nasadit aplikaci.  
  
 Všechny následující kroky konfigurace lze provádět pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Pro zdrojovou kopii tohoto příkladu, naleznete v tématu [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Chcete-li určit BasicHttpBinding použít ke konfiguraci služby  
  
1. Definování kontraktu služby pro typ služby.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. Implementace kontraktu služby ve třídě služby.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  Informace o adresu nebo vazby není zadán uvnitř implementace služby. Kód také nemá k zapsání k načtení těchto informací z konfiguračního souboru.  
  
3. Vytvořit soubor Web.config pro konfigurace koncového bodu `CalculatorService` , která používá <xref:System.ServiceModel.WSHttpBinding>.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <!-- Leave the address blank to be populated by default -->  
            <!-- from the hosting environment,in this case IIS, so -->  
            <!-- the address will just be that of the IIS Virtual -->  
            <!-- Directory. -->  
                address=""   
            <!-- Specify the binding type -->  
                binding="wsHttpBinding"  
            <!-- Specify the binding configuration name for that -->  
            <!-- binding type. This is optional but useful if you -->  
            <!-- want to modify the properties of the binding. -->  
            <!-- The bindingConfiguration name Binding1 is defined -->  
            <!-- below in the bindings element. -->  
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
  
4. Vytvořte Service.svc soubor, který obsahuje následující řádek a umístěte ho do virtuálního adresáře Internetové informační služby (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Chcete-li změnit výchozí hodnoty vlastností vazby  
  
1. Upravit některou výchozí hodnoty vlastností <xref:System.ServiceModel.WSHttpBinding>, vytvořte nový název konfigurace vazby – `<binding name="Binding1">` – v rámci [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu a nastavte nové hodnoty pro atributy Vazba v tomto elementu vazby. Například pokud chcete změnit výchozí otevřít a zavřít hodnoty časového limitu minutu až 2 minuty, přidejte následující konfigurační soubor.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
