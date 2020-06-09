---
title: 'Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 9acefdec63a6f518ead6cdbcb19ebc8c75609dd6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595359"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby
Svcutil. exe může exportovat metadata pro služby, kontrakty a datové typy v kompilovaných sestaveních následujícím způsobem:  
  
- Chcete-li exportovat metadata pro všechny smlouvy zkompilované služby pro sadu sestavení pomocí Svcutil. exe, zadejte sestavení jako vstupní parametry. Toto je výchozí chování.  
  
- Chcete-li exportovat metadata pro kompilovaná službu pomocí Svcutil. exe, zadejte jako vstupní parametry sestavení služby nebo sestavení. `/serviceName`K určení názvu konfigurace služby, kterou chcete exportovat, je nutné použít možnost. Svcutil. exe automaticky načte konfigurační soubor pro zadané spustitelné sestavení.  
  
- Chcete-li exportovat všechny typy kontraktů dat v rámci sady sestavení, použijte `/dataContractOnly` možnost.  
  
> [!NOTE]
> Použijte `/reference` možnost k zadání cest k souborům pro všechna závislá sestavení.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Export metadat pro zkompilované kontrakty služby  
  
1. Zkompilujte implementace kontraktu služby do jedné nebo více knihoven tříd. 1  
  
2. Spusťte Svcutil. exe na kompilovaných sestaveních.  
  
    > [!NOTE]
    > Možná budete muset použít `/reference` přepínač a zadat cestu k souboru pro všechna závislá sestavení.  
  
    ```console
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
  
    ```console  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Export metadat pro kontrakty kompilovaných dat  
  
1. Zkompilujte implementace kontraktů dat do jedné nebo více knihoven tříd.  
  
2. Spusťte Svcutil. exe na kompilovaných sestaveních pomocí `/dataContract` přepínače a určete tak, že se mají vygenerovat jenom metadata pro kontrakty dat.  
  
    > [!NOTE]
    > Možná budete muset použít `/reference` přepínač a zadat cestu k souboru pro všechna závislá sestavení.  
  
    ```console  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak generovat metadata pro jednoduchou implementaci a konfiguraci služby.  
  
 Pro export metadat pro kontrakt služby.  
  
```console  
svcutil.exe Contracts.dll  
```  
  
 Pro export metadat pro kontrakty dat.  
  
```console  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 Pro export metadat pro implementaci služby.  
  
```console  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 `<path>`Je cesta ke smlouvám. dll.  
  
```csharp
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
```

```csharp
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
```

```xml  
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

- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Export a import metadat](exporting-and-importing-metadata.md)
