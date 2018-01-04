---
title: "Postupy: Zadání vazby služby v konfiguraci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea54b2f84c9de233ff2560795dc97f79c15aa0af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Postupy: Zadání vazby služby v konfiguraci
V tomto příkladu `ICalculator` kontrakt je definována pro službu základní kalkulačky, služba se implementuje v `CalculatorService` třídě a následně svůj koncový bod je nakonfigurován v souboru Web.config, kde je zadán, že služba používá <xref:System.ServiceModel.BasicHttpBinding> . Popis toho, jak nakonfigurovat tuto službu pomocí kódu místo konfigurace, najdete v části [postupy: zadání vazby služby v kódu](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).  
  
 Obvykle je osvědčeným postupem zadejte vazby a informace o adrese deklarativně v konfiguraci, nikoli imperativní v kódu. Definování koncové body v kódu obvykle není praktické protože jsou obvykle liší od těch, které používá při služby je vyvíjen vazeb a adresy pro v nasazené službě. Obecně platí udržování vazby a adresování informace mimo kód jim umožňuje změnit bez nutnosti znovu zkompiluje nebo znovu nasadit aplikaci.  
  
 Všechny tyto kroky konfigurace lze provádět pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Zdroj kopírování tohoto příkladu, najdete v části [základní vazby](../../../docs/framework/wcf/samples/basicbinding.md).  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Chcete-li určit BasicHttpBinding použít ke konfiguraci služby  
  
1.  Definování kontraktu služby pro typ služby.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  Implementujte kontrakt služby v třídě služby.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  Informace o adresu nebo vazba není zadat v rámci implementace služby. Kód také nemá k zapsání k načtení těchto informací z konfiguračního souboru.  
  
3.  Vytvoření souboru Web.config, který konfigurace koncového bodu `CalculatorService` používající <xref:System.ServiceModel.WSHttpBinding>.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <-- Leave the address blank to be populated by default-->  
            <--from the hosting environment,in this case IIS, so -->  
            <-- the address will just be that of the IIS Virtual -->  
            <--Directory.-->  
                address=""   
            <--Specify the binding type -->  
                binding="wsHttpBinding"  
            <--Specify the binding configuration name for that -->  
            <--binding type. This is optional but useful if you  -->  
            <--want to modify the properties of the binding. -->  
            <--The bindingConfiguration name Binding1 is defined  -->  
            <--below in the bindings element.  -->  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <-- Binding property values can be modified here. -->  
              <--See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  Vytvořte soubor Service.svc, který obsahuje následující řádek a jeho následné uložení do virtuálního adresáře Internetové informační služby (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Chcete-li změnit výchozí hodnoty vlastností vazby  
  
1.  K úpravě jeden z výchozí hodnoty vlastností <xref:System.ServiceModel.WSHttpBinding>, vytvořte nový název konfigurace vazby - `<binding name="Binding1">` – v [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element a nastavte nové hodnoty pro atributy Vazba v tomto elementu vazby. Například změnit výchozí otevřete a zavřete hodnoty časového limitu 1 minutu 2 minuty, přidejte následující do konfiguračního souboru.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
