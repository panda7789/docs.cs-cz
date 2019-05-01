---
title: 'Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 5b905b6943127d483e001749c263242550ab28ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047332"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby
Metadata pro služby, kontrakty a datové typy v kompilovaných sestavení, můžete exportovat svcutil.exe následujícím způsobem:  
  
- Pro export metadat pro všechny zkompilován kontraktů služby pro sadu sestavení pomocí Svcutil.exe, zadejte sestavení jako vstupní parametry. Toto je výchozí chování.  
  
- Pro export metadat pro kompilované služby pomocí Svcutil.exe, zadejte jako vstupní parametry služby sestavení nebo sestavení. Je nutné použít `/serviceName` možnost určíte název konfigurace služby, kterou chcete exportovat. Svcutil.exe automaticky načte konfigurační soubor pro zadaného spustitelného sestavení.  
  
- Chcete-li exportovat všechny typy kontraktu dat v rámci sestavení, použijte `/dataContractOnly` možnost.  
  
> [!NOTE]
>  Použití `/reference` možnost určení cesty k souborům pro všechna závislá sestavení.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Pro export metadat pro kompilaci kontrakty služeb  
  
1. Kompilace vaší implementace kontraktu služby do jednoho nebo více tříd libraries.1  
  
2. Spusťte Svcutil.exe v kompilovaných sestavení.  
  
    > [!NOTE]
    >  Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru pro všechna závislá sestavení.  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Pro export metadat pro kompilované služby  
  
1. Zkompilujte vaše implementace služby do spustitelného sestavení.  
  
2. Vytvoření konfiguračního souboru pro spustitelný soubor vaší služby a přidejte konfigurace služby.  
  
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
  
3. Spustili spustitelný soubor zkompilovaný služby pomocí Svcutil.exe `/serviceName` přepínač k určení názvu konfigurace služby.  
  
    > [!NOTE]
    >  Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru pro všechna závislá sestavení.  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Pro export metadat pro kompilaci kontraktů dat  
  
1. Zkompilujte vaší implementace kontraktu dat do jednoho nebo více knihoven tříd.  
  
2. Spustit v kompilovaných sestavení pomocí Svcutil.exe `/dataContract` přepínač pro určení této pouze metadata kontraktů dat by měl být vygenerován.  
  
    > [!NOTE]
    >  Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru pro všechna závislá sestavení.  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak generovat metadata pro implementaci jednoduchého služby a konfiguraci.  
  
 Pro export metadat pro kontrakt služby.  
  
```  
svcutil.exe Contracts.dll  
```  
  
 Pro export metadat pro kontrakty dat.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
