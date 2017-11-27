---
title: "Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 444fab903683b952d1a8c312c3f6032be880da68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby
Metadata pro služby, smlouvy a datových typů v sestaveních kompilované, můžete exportovat svcutil.exe následujícím způsobem:  
  
-   Sestavení pro export metadat pro všechny zkompilovat kontraktů služby pro sadu sestavení s využitím Svcutil.exe, zadejte jako vstupní parametry. Toto je výchozí chování.  
  
-   Pro export metadat pro kompilované služby pomocí nástroje Svcutil.exe, zadejte jako vstupní parametry servisní sestavení nebo sestavení. Je nutné použít `/serviceName` možnost určíte název konfigurace služby, kterou chcete exportovat. Svcutil.exe automaticky načte konfiguračního souboru pro zadaný spustitelný soubor sestavení.  
  
-   Chcete-li exportovat všechny typy kontraktů dat v rámci sady sestavení, použijte `/dataContractOnly` možnost.  
  
> [!NOTE]
>  Použití `/reference` možnost určení cesty k souborům na všechny závislé sestavení.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Pro export metadat pro zkompilovat kontraktů služby  
  
1.  Kompilace vaší implementace kontraktu služby do jednoho nebo více libraries.1 – třída  
  
2.  Spusťte Svcutil.exe kompilované sestavení.  
  
    > [!NOTE]
    >  Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru na všechny závislé sestavení.  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Pro export metadat kompilované služby  
  
1.  Zkompilujte implementaci služby do spustitelného souboru sestavení.  
  
2.  Vytvořte konfigurační soubor pro vaše spustitelný soubor služby a přidejte konfigurace služby.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3.  Spustit Svcutil.exe na spustitelný soubor kompilované služby pomocí `/serviceName` přepínač tak, aby zadejte název konfigurace služby.  
  
    > [!NOTE]
    >  Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru na všechny závislé sestavení.  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Pro export metadat pro zkompilovat kontrakty dat  
  
1.  Zkompilujte vaší implementace kontraktu dat do jednoho nebo více knihovny tříd.  
  
2.  Spustit Svcutil.exe kompilované sestavení pomocí `/dataContract` přepínač tak, aby zadat aby pouze metadata kontrakty dat by měl být vygenerován.  
  
    > [!NOTE]
    >  Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru na všechny závislé sestavení.  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak generovat metadata pro implementaci jednoduché služby a konfiguraci.  
  
 Pro export metadat pro kontrakt služby.  
  
```  
svcutil.exe Contracts.dll  
```  
  
 Pro export metadat pro data smlouvy.  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 Pro export metadat pro implementaci služby.  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 `<path>` Je cesta k Contracts.dll.  
  
```  
// The following service contract and data contracts are compiled into   
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
  
// The following service implementation is compiled into Service.exe.     
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
