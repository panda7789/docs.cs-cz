---
title: 'Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: b8ddbaf896ee4c6ea8b6f8e8ce7d0ecef28140ea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932573"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby
Svcutil. exe může exportovat metadata pro služby, kontrakty a datové typy v kompilovaných sestaveních následujícím způsobem:  
  
- Chcete-li exportovat metadata pro všechny smlouvy zkompilované služby pro sadu sestavení pomocí Svcutil. exe, zadejte sestavení jako vstupní parametry. Toto je výchozí chování.  
  
- Chcete-li exportovat metadata pro kompilovaná službu pomocí Svcutil. exe, zadejte jako vstupní parametry sestavení služby nebo sestavení. K určení názvu konfigurace `/serviceName` služby, kterou chcete exportovat, je nutné použít možnost. Svcutil. exe automaticky načte konfigurační soubor pro zadané spustitelné sestavení.  
  
- Chcete-li exportovat všechny typy kontraktů dat v rámci sady sestavení, `/dataContractOnly` použijte možnost.  
  
> [!NOTE]
> `/reference` Použijte možnost k zadání cest k souborům pro všechna závislá sestavení.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Export metadat pro zkompilované kontrakty služby  
  
1. Zkompilujte implementace kontraktu služby do jedné nebo více knihoven tříd. 1  
  
2. Spusťte Svcutil. exe na kompilovaných sestaveních.  
  
    > [!NOTE]
    > Možná budete muset použít `/reference` přepínač a zadat cestu k souboru pro všechna závislá sestavení.  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Export metadat pro zkompilované služby  
  
1. Zkompilujte implementaci služby do spustitelného sestavení.  
  
2. Vytvořte konfigurační soubor pro spustitelný soubor služby a přidejte konfiguraci služby.  
  
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
  
3. Spusťte Svcutil. exe ve spustitelném souboru zkompilované služby pomocí `/serviceName` přepínače, který určuje název konfigurace služby.  
  
    > [!NOTE]
    > Možná budete muset použít `/reference` přepínač a zadat cestu k souboru pro všechna závislá sestavení.  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Export metadat pro kontrakty kompilovaných dat  
  
1. Zkompilujte implementace kontraktů dat do jedné nebo více knihoven tříd.  
  
2. Spusťte Svcutil. exe na kompilovaných sestaveních pomocí `/dataContract` přepínače a určete tak, že se mají vygenerovat jenom metadata pro kontrakty dat.  
  
    > [!NOTE]
    > Možná budete muset použít `/reference` přepínač a zadat cestu k souboru pro všechna závislá sestavení.  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak generovat metadata pro jednoduchou implementaci a konfiguraci služby.  
  
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
  
 `<path>` Je cesta ke smlouvám. dll.  
  
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
