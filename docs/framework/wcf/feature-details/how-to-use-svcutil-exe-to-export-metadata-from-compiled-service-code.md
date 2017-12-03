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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b6998333c3e49b24ad5bb96f36be65af94b6033
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="c09cf-102">Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby</span><span class="sxs-lookup"><span data-stu-id="c09cf-102">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>
<span data-ttu-id="c09cf-103">Metadata pro služby, smlouvy a datových typů v sestaveních kompilované, můžete exportovat svcutil.exe následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c09cf-103">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
-   <span data-ttu-id="c09cf-104">Sestavení pro export metadat pro všechny zkompilovat kontraktů služby pro sadu sestavení s využitím Svcutil.exe, zadejte jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="c09cf-104">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="c09cf-105">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="c09cf-105">This is the default behavior.</span></span>  
  
-   <span data-ttu-id="c09cf-106">Pro export metadat pro kompilované služby pomocí nástroje Svcutil.exe, zadejte jako vstupní parametry servisní sestavení nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="c09cf-106">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="c09cf-107">Je nutné použít `/serviceName` možnost určíte název konfigurace služby, kterou chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="c09cf-107">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="c09cf-108">Svcutil.exe automaticky načte konfiguračního souboru pro zadaný spustitelný soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="c09cf-108">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
-   <span data-ttu-id="c09cf-109">Chcete-li exportovat všechny typy kontraktů dat v rámci sady sestavení, použijte `/dataContractOnly` možnost.</span><span class="sxs-lookup"><span data-stu-id="c09cf-109">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c09cf-110">Použití `/reference` možnost určení cesty k souborům na všechny závislé sestavení.</span><span class="sxs-lookup"><span data-stu-id="c09cf-110">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="c09cf-111">Pro export metadat pro zkompilovat kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="c09cf-111">To export metadata for compiled service contracts</span></span>  
  
1.  <span data-ttu-id="c09cf-112">Kompilace vaší implementace kontraktu služby do jednoho nebo více libraries.1 – třída</span><span class="sxs-lookup"><span data-stu-id="c09cf-112">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2.  <span data-ttu-id="c09cf-113">Spusťte Svcutil.exe kompilované sestavení.</span><span class="sxs-lookup"><span data-stu-id="c09cf-113">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c09cf-114">Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru na všechny závislé sestavení.</span><span class="sxs-lookup"><span data-stu-id="c09cf-114">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="c09cf-115">Pro export metadat kompilované služby</span><span class="sxs-lookup"><span data-stu-id="c09cf-115">To export metadata for a compiled service</span></span>  
  
1.  <span data-ttu-id="c09cf-116">Zkompilujte implementaci služby do spustitelného souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="c09cf-116">Compile your service implementation into an executable assembly.</span></span>  
  
2.  <span data-ttu-id="c09cf-117">Vytvořte konfigurační soubor pro vaše spustitelný soubor služby a přidejte konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="c09cf-117">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
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
  
3.  <span data-ttu-id="c09cf-118">Spustit Svcutil.exe na spustitelný soubor kompilované služby pomocí `/serviceName` přepínač tak, aby zadejte název konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="c09cf-118">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c09cf-119">Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru na všechny závislé sestavení.</span><span class="sxs-lookup"><span data-stu-id="c09cf-119">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="c09cf-120">Pro export metadat pro zkompilovat kontrakty dat</span><span class="sxs-lookup"><span data-stu-id="c09cf-120">To export metadata for compiled data contracts</span></span>  
  
1.  <span data-ttu-id="c09cf-121">Zkompilujte vaší implementace kontraktu dat do jednoho nebo více knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="c09cf-121">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2.  <span data-ttu-id="c09cf-122">Spustit Svcutil.exe kompilované sestavení pomocí `/dataContract` přepínač tak, aby zadat aby pouze metadata kontrakty dat by měl být vygenerován.</span><span class="sxs-lookup"><span data-stu-id="c09cf-122">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c09cf-123">Možná budete muset použít `/reference` přepínač tak, aby zadejte cestu k souboru na všechny závislé sestavení.</span><span class="sxs-lookup"><span data-stu-id="c09cf-123">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="c09cf-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="c09cf-124">Example</span></span>  
 <span data-ttu-id="c09cf-125">Následující příklad ukazuje, jak generovat metadata pro implementaci jednoduché služby a konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c09cf-125">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="c09cf-126">Pro export metadat pro kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="c09cf-126">To export metadata for the service contract.</span></span>  
  
```  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="c09cf-127">Pro export metadat pro data smlouvy.</span><span class="sxs-lookup"><span data-stu-id="c09cf-127">To export metadata for the data contracts.</span></span>  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="c09cf-128">Pro export metadat pro implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="c09cf-128">To export metadata for the service implementation.</span></span>  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="c09cf-129">`<path>` Je cesta k Contracts.dll.</span><span class="sxs-lookup"><span data-stu-id="c09cf-129">The `<path>` is the path to Contracts.dll.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c09cf-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="c09cf-130">See Also</span></span>  
 [<span data-ttu-id="c09cf-131">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="c09cf-131">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="c09cf-132">Export a import metadat</span><span class="sxs-lookup"><span data-stu-id="c09cf-132">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
