---
title: 'Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: b6f010cb5edc3111f05c78f5d27cf178bd501ef9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326421"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="d7dfe-102">Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="d7dfe-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="d7dfe-103">Služby a klientské aplikace, které používají datové typy, které jsou serializovatelné pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilaci kódu serializace pro typy dat za běhu, což může vést k pomalé spouštění výkonu.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7dfe-104">Předem generovaného Serializační kód jde použít jenom v klientských aplikacích a ne v služeb.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="d7dfe-105">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) výkon lze zvýšit objem požadovaný při spuštění pro tyto aplikace generování kódu serializace nezbytné ze zkompilovaných sestavení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="d7dfe-106">Generuje kód serializace pro všechny datové typy používané v kontraktech služeb v sestavení kompilované aplikace, které lze serializovat pomocí svcutil.exe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d7dfe-107">Služby a operace smluv, které používají <xref:System.Xml.Serialization.XmlSerializer> jsou označené <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="d7dfe-108">Ke generování kódu serializace XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="d7dfe-108">To generate XmlSerializer serialization code</span></span>  
  
1. <span data-ttu-id="d7dfe-109">Kompilaci kódu služby ani klienta do jednoho nebo více sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2. <span data-ttu-id="d7dfe-110">Otevřete příkazový řádek sady SDK.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-110">Open an SDK command prompt.</span></span>  
  
3. <span data-ttu-id="d7dfe-111">Na příkazovém řádku spusťte nástroje Svcutil.exe v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="d7dfe-112">`assemblyPath` Argument určuje cestu k sestavení, který obsahuje typy kontraktů služby.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="d7dfe-113">Generuje kód serializace pro všechny datové typy používané v kontraktech služeb v sestavení kompilované aplikace, které lze serializovat pomocí svcutil.exe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="d7dfe-114">Svcutil.exe lze generovat C# Serializační kód.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="d7dfe-115">Jeden soubor zdrojového kódu se generuje pro každý vstupní sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="d7dfe-116">Nelze použít **/language** přepínači změnit jazyk generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="d7dfe-117">Chcete-li zadat cestu k závislá sestavení, použijte **/reference** možnost.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4. <span data-ttu-id="d7dfe-118">Kód vygenerovaný serializace zpřístupnit do vaší aplikace pomocí jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="d7dfe-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1.  <span data-ttu-id="d7dfe-119">Kompilace generovaného Serializační kód do samostatné sestavení s názvem [*původní sestavení*]. XmlSerializers.dll (například MyApp.XmlSerializers.dll).</span><span class="sxs-lookup"><span data-stu-id="d7dfe-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="d7dfe-120">Aplikace musí být schopný načíst sestavení, které musí být podepsané stejným klíčem jako původní sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="d7dfe-121">Pokud je provedena rekompilace původní sestavení, je třeba znovu vygenerovat sestavení serializace.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2.  <span data-ttu-id="d7dfe-122">Kompilace generovaného Serializační kód do samostatné sestavení a použít <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> v kontraktu služby, který používá <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="d7dfe-123">Nastavte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> nebo <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> vlastnosti tak, aby odkazoval na kompilované serializace sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3.  <span data-ttu-id="d7dfe-124">Kompilace generovaného Serializační kód do vašeho sestavení aplikace a přidat <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> pro servisní smlouvy, které používá <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="d7dfe-125">Nenastavujte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> nebo <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="d7dfe-126">Výchozí sestavení serializace je považován za aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="d7dfe-127">Ke generování kódu serializace XmlSerializer v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d7dfe-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1. <span data-ttu-id="d7dfe-128">Vytvoření klienta a služby WCF projekty v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="d7dfe-129">Nakonec přidejte odkaz na službu do projektu klienta.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-129">Then, add a service reference to the client project.</span></span>  
  
2. <span data-ttu-id="d7dfe-130">Přidat <xref:System.ServiceModel.XmlSerializerFormatAttribute> ke kontraktu služby ve *reference.cs* soubor v projektu aplikace klienta v části **serviceReference** -> **reference.svcmap** .</span><span class="sxs-lookup"><span data-stu-id="d7dfe-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="d7dfe-131">Všimněte si, že potřebujete zobrazit všechny soubory v **Průzkumníka řešení** zobrazíte tyto soubory.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3. <span data-ttu-id="d7dfe-132">Vytvořte klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-132">Build the client app.</span></span>  
  
4. <span data-ttu-id="d7dfe-133">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření předem generovaného serializátoru *.cs* soubor pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="d7dfe-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="d7dfe-134">AssemblyPath argument určuje cestu k sestavení klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="d7dfe-135">Například:</span><span class="sxs-lookup"><span data-stu-id="d7dfe-135">Such as:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="d7dfe-136">*WCFClient.XmlSerializers.dll.cs* vygeneruje soubor.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5. <span data-ttu-id="d7dfe-137">Kompilace sestavení serializace předem generovaného.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="d7dfe-138">Na základě příkladu v předchozím kroku, příkaz compile by byl následující:</span><span class="sxs-lookup"><span data-stu-id="d7dfe-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="d7dfe-139">Ujistěte se, že generované *WCFClient.XmlSerializers.dll* je ve stejném adresáři jako klientskou aplikaci, která je *WCFClient.exe* v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6. <span data-ttu-id="d7dfe-140">Spuštění klientské aplikace jako obvykle.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-140">Run the client app as usual.</span></span> <span data-ttu-id="d7dfe-141">Sestavení serializace předem generovaného se použije.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7dfe-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7dfe-142">Example</span></span>  
 <span data-ttu-id="d7dfe-143">Následující příkaz vygeneruje typy serializace pro `XmlSerializer` typy, které službám smluv týkajících se použití sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7dfe-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7dfe-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7dfe-144">See also</span></span>

- [<span data-ttu-id="d7dfe-145">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d7dfe-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
