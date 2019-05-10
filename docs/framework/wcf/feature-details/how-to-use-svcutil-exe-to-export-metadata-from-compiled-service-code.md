---
title: 'Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 40c684cbc1b14bf14d3ca23cbc044020e36b85f1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650232"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="1fb32-102">Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby</span><span class="sxs-lookup"><span data-stu-id="1fb32-102">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>
<span data-ttu-id="1fb32-103">Metadata pro služby, kontrakty a datové typy v kompilovaných sestavení, můžete exportovat svcutil.exe následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1fb32-103">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
- <span data-ttu-id="1fb32-104">Pro export metadat pro všechny zkompilován kontraktů služby pro sadu sestavení pomocí Svcutil.exe, zadejte sestavení jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="1fb32-104">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="1fb32-105">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="1fb32-105">This is the default behavior.</span></span>  
  
- <span data-ttu-id="1fb32-106">Pro export metadat pro kompilované služby pomocí Svcutil.exe, zadejte jako vstupní parametry služby sestavení nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fb32-106">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="1fb32-107">Je nutné použít `/serviceName` možnost určíte název konfigurace služby, kterou chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="1fb32-107">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="1fb32-108">Svcutil.exe automaticky načte konfigurační soubor pro zadaného spustitelného sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fb32-108">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
- <span data-ttu-id="1fb32-109">Chcete-li exportovat všechny typy kontraktu dat v rámci sestavení, použijte `/dataContractOnly` možnost.</span><span class="sxs-lookup"><span data-stu-id="1fb32-109">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fb32-110">Použití `/reference` možnost určení cesty k souborům pro všechna závislá sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fb32-110">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="1fb32-111">Pro export metadat pro kompilaci kontrakty služeb</span><span class="sxs-lookup"><span data-stu-id="1fb32-111">To export metadata for compiled service contracts</span></span>  
  
1. <span data-ttu-id="1fb32-112">Kompilace vaší implementace kontraktu služby do jednoho nebo více tříd libraries.1</span><span class="sxs-lookup"><span data-stu-id="1fb32-112">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2. <span data-ttu-id="1fb32-113">Spusťte Svcutil.exe v kompilovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fb32-113">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1fb32-114">Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru pro všechna závislá sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fb32-114">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="1fb32-115">Pro export metadat pro kompilované služby</span><span class="sxs-lookup"><span data-stu-id="1fb32-115">To export metadata for a compiled service</span></span>  
  
1. <span data-ttu-id="1fb32-116">Zkompilujte vaše implementace služby do spustitelného sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fb32-116">Compile your service implementation into an executable assembly.</span></span>  
  
2. <span data-ttu-id="1fb32-117">Vytvoření konfiguračního souboru pro spustitelný soubor vaší služby a přidejte konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="1fb32-117">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
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
  
3. <span data-ttu-id="1fb32-118">Spustili spustitelný soubor zkompilovaný služby pomocí Svcutil.exe `/serviceName` přepínač k určení názvu konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="1fb32-118">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1fb32-119">Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru pro všechna závislá sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fb32-119">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="1fb32-120">Pro export metadat pro kompilaci kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="1fb32-120">To export metadata for compiled data contracts</span></span>  
  
1. <span data-ttu-id="1fb32-121">Zkompilujte vaší implementace kontraktu dat do jednoho nebo více knihoven tříd.</span><span class="sxs-lookup"><span data-stu-id="1fb32-121">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2. <span data-ttu-id="1fb32-122">Spustit v kompilovaných sestavení pomocí Svcutil.exe `/dataContract` přepínač pro určení této pouze metadata kontraktů dat by měl být vygenerován.</span><span class="sxs-lookup"><span data-stu-id="1fb32-122">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1fb32-123">Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru pro všechna závislá sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fb32-123">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="1fb32-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fb32-124">Example</span></span>  
 <span data-ttu-id="1fb32-125">Následující příklad ukazuje, jak generovat metadata pro implementaci jednoduchého služby a konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="1fb32-125">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="1fb32-126">Pro export metadat pro kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="1fb32-126">To export metadata for the service contract.</span></span>  
  
```  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="1fb32-127">Pro export metadat pro kontrakty dat.</span><span class="sxs-lookup"><span data-stu-id="1fb32-127">To export metadata for the data contracts.</span></span>  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="1fb32-128">Pro export metadat pro implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="1fb32-128">To export metadata for the service implementation.</span></span>  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="1fb32-129">`<path>` Je cesta k Contracts.dll.</span><span class="sxs-lookup"><span data-stu-id="1fb32-129">The `<path>` is the path to Contracts.dll.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1fb32-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1fb32-130">See also</span></span>

- [<span data-ttu-id="1fb32-131">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="1fb32-131">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="1fb32-132">Export a import metadat</span><span class="sxs-lookup"><span data-stu-id="1fb32-132">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
