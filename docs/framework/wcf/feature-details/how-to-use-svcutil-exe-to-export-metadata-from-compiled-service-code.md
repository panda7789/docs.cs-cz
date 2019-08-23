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
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="5218d-102">Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby</span><span class="sxs-lookup"><span data-stu-id="5218d-102">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>
<span data-ttu-id="5218d-103">Svcutil. exe může exportovat metadata pro služby, kontrakty a datové typy v kompilovaných sestaveních následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5218d-103">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
- <span data-ttu-id="5218d-104">Chcete-li exportovat metadata pro všechny smlouvy zkompilované služby pro sadu sestavení pomocí Svcutil. exe, zadejte sestavení jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="5218d-104">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="5218d-105">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="5218d-105">This is the default behavior.</span></span>  
  
- <span data-ttu-id="5218d-106">Chcete-li exportovat metadata pro kompilovaná službu pomocí Svcutil. exe, zadejte jako vstupní parametry sestavení služby nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="5218d-106">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="5218d-107">K určení názvu konfigurace `/serviceName` služby, kterou chcete exportovat, je nutné použít možnost.</span><span class="sxs-lookup"><span data-stu-id="5218d-107">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="5218d-108">Svcutil. exe automaticky načte konfigurační soubor pro zadané spustitelné sestavení.</span><span class="sxs-lookup"><span data-stu-id="5218d-108">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
- <span data-ttu-id="5218d-109">Chcete-li exportovat všechny typy kontraktů dat v rámci sady sestavení, `/dataContractOnly` použijte možnost.</span><span class="sxs-lookup"><span data-stu-id="5218d-109">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5218d-110">`/reference` Použijte možnost k zadání cest k souborům pro všechna závislá sestavení.</span><span class="sxs-lookup"><span data-stu-id="5218d-110">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="5218d-111">Export metadat pro zkompilované kontrakty služby</span><span class="sxs-lookup"><span data-stu-id="5218d-111">To export metadata for compiled service contracts</span></span>  
  
1. <span data-ttu-id="5218d-112">Zkompilujte implementace kontraktu služby do jedné nebo více knihoven tříd. 1</span><span class="sxs-lookup"><span data-stu-id="5218d-112">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2. <span data-ttu-id="5218d-113">Spusťte Svcutil. exe na kompilovaných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="5218d-113">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5218d-114">Možná budete muset použít `/reference` přepínač a zadat cestu k souboru pro všechna závislá sestavení.</span><span class="sxs-lookup"><span data-stu-id="5218d-114">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="5218d-115">Export metadat pro zkompilované služby</span><span class="sxs-lookup"><span data-stu-id="5218d-115">To export metadata for a compiled service</span></span>  
  
1. <span data-ttu-id="5218d-116">Zkompilujte implementaci služby do spustitelného sestavení.</span><span class="sxs-lookup"><span data-stu-id="5218d-116">Compile your service implementation into an executable assembly.</span></span>  
  
2. <span data-ttu-id="5218d-117">Vytvořte konfigurační soubor pro spustitelný soubor služby a přidejte konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="5218d-117">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
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
  
3. <span data-ttu-id="5218d-118">Spusťte Svcutil. exe ve spustitelném souboru zkompilované služby pomocí `/serviceName` přepínače, který určuje název konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="5218d-118">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5218d-119">Možná budete muset použít `/reference` přepínač a zadat cestu k souboru pro všechna závislá sestavení.</span><span class="sxs-lookup"><span data-stu-id="5218d-119">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="5218d-120">Export metadat pro kontrakty kompilovaných dat</span><span class="sxs-lookup"><span data-stu-id="5218d-120">To export metadata for compiled data contracts</span></span>  
  
1. <span data-ttu-id="5218d-121">Zkompilujte implementace kontraktů dat do jedné nebo více knihoven tříd.</span><span class="sxs-lookup"><span data-stu-id="5218d-121">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2. <span data-ttu-id="5218d-122">Spusťte Svcutil. exe na kompilovaných sestaveních pomocí `/dataContract` přepínače a určete tak, že se mají vygenerovat jenom metadata pro kontrakty dat.</span><span class="sxs-lookup"><span data-stu-id="5218d-122">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5218d-123">Možná budete muset použít `/reference` přepínač a zadat cestu k souboru pro všechna závislá sestavení.</span><span class="sxs-lookup"><span data-stu-id="5218d-123">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="5218d-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="5218d-124">Example</span></span>  
 <span data-ttu-id="5218d-125">Následující příklad ukazuje, jak generovat metadata pro jednoduchou implementaci a konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="5218d-125">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="5218d-126">Pro export metadat pro kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="5218d-126">To export metadata for the service contract.</span></span>  
  
```  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="5218d-127">Pro export metadat pro kontrakty dat.</span><span class="sxs-lookup"><span data-stu-id="5218d-127">To export metadata for the data contracts.</span></span>  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="5218d-128">Pro export metadat pro implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="5218d-128">To export metadata for the service implementation.</span></span>  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="5218d-129">`<path>` Je cesta ke smlouvám. dll.</span><span class="sxs-lookup"><span data-stu-id="5218d-129">The `<path>` is the path to Contracts.dll.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5218d-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5218d-130">See also</span></span>

- [<span data-ttu-id="5218d-131">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="5218d-131">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="5218d-132">Export a import metadat</span><span class="sxs-lookup"><span data-stu-id="5218d-132">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
