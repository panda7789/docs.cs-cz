---
title: 'Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: ca15d710a30586135f0d030e155b09b63a22ee45
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976054"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="694fb-102">Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="694fb-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="694fb-103">Služby a klientské aplikace, které používají datové typy, které jsou serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer> generovat a kompilovat serializaci kódu pro tyto datové typy za běhu, což může vést k pomalému spuštění výkonu.</span><span class="sxs-lookup"><span data-stu-id="694fb-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="694fb-104">Předem generovaný kód serializace lze použít pouze v klientských aplikacích, nikoli v službách.</span><span class="sxs-lookup"><span data-stu-id="694fb-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="694fb-105">Nástroj pro měření [metadat třídy (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) může zlepšit výkon spuštění těchto aplikací vygenerováním potřebného kódu serializace z kompilovaných sestavení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="694fb-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="694fb-106">Svcutil. exe generuje kód serializace pro všechny datové typy, které se používají v rámci kontraktů služby v sestavení zkompilované aplikace, které lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="694fb-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="694fb-107">Kontrakty služeb a operace, které používají <xref:System.Xml.Serialization.XmlSerializer>, jsou označené <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="694fb-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="694fb-108">Pro generování kódu serializace XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="694fb-108">To generate XmlSerializer serialization code</span></span>  
  
1. <span data-ttu-id="694fb-109">Zkompilujte kód služby nebo klienta do jednoho nebo více sestavení.</span><span class="sxs-lookup"><span data-stu-id="694fb-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2. <span data-ttu-id="694fb-110">Otevřete příkazový řádek sady SDK.</span><span class="sxs-lookup"><span data-stu-id="694fb-110">Open an SDK command prompt.</span></span>  
  
3. <span data-ttu-id="694fb-111">Na příkazovém řádku spusťte nástroj Svcutil. exe v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="694fb-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="694fb-112">Argument `assemblyPath` Určuje cestu k sestavení, které obsahuje typy kontraktů služby.</span><span class="sxs-lookup"><span data-stu-id="694fb-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="694fb-113">Svcutil. exe generuje kód serializace pro všechny datové typy, které se používají v rámci kontraktů služby v sestavení zkompilované aplikace, které lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="694fb-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="694fb-114">Svcutil. exe může generovat C# pouze Serializační kód.</span><span class="sxs-lookup"><span data-stu-id="694fb-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="694fb-115">Jeden soubor zdrojového kódu je vygenerován pro každé vstupní sestavení.</span><span class="sxs-lookup"><span data-stu-id="694fb-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="694fb-116">Nelze použít přepínač **/Language** ke změně jazyka generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="694fb-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="694fb-117">Chcete-li zadat cestu k závislým sestavením, použijte možnost **/reference** .</span><span class="sxs-lookup"><span data-stu-id="694fb-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4. <span data-ttu-id="694fb-118">Zpřístupněte generovaný kód serializace vaší aplikaci pomocí jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="694fb-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1. <span data-ttu-id="694fb-119">Zkompilujte generovaný kód serializace do samostatného sestavení s názvem [*původní sestavení*]. XmlSerializers. dll (například MyApp. XmlSerializers. dll).</span><span class="sxs-lookup"><span data-stu-id="694fb-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="694fb-120">Vaše aplikace musí být schopna načíst sestavení, které musí být podepsáno stejným klíčem jako původní sestavení.</span><span class="sxs-lookup"><span data-stu-id="694fb-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="694fb-121">Pokud znovu zkompilujete původní sestavení, je nutné znovu vygenerovat sestavení serializace.</span><span class="sxs-lookup"><span data-stu-id="694fb-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2. <span data-ttu-id="694fb-122">Zkompilujte generovaný kód serializace do samostatného sestavení a použijte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> v kontraktu služby, který používá <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="694fb-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="694fb-123">Nastavte vlastnosti <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> nebo <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> tak, aby odkazovaly na zkompilované sestavení serializace.</span><span class="sxs-lookup"><span data-stu-id="694fb-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3. <span data-ttu-id="694fb-124">Zkompilujte generovaný kód serializace do sestavení aplikace a přidejte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> do kontraktu služby, který používá <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="694fb-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="694fb-125">Nenastavte vlastnosti <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ani <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="694fb-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="694fb-126">Výchozí sestavení serializace je považováno za aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="694fb-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="694fb-127">Generování kódu serializace XmlSerializer v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="694fb-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1. <span data-ttu-id="694fb-128">Vytvořte v aplikaci Visual Studio službu WCF a klientské projekty.</span><span class="sxs-lookup"><span data-stu-id="694fb-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="694fb-129">Pak přidejte odkaz na službu do klientského projektu.</span><span class="sxs-lookup"><span data-stu-id="694fb-129">Then, add a service reference to the client project.</span></span>  
  
2. <span data-ttu-id="694fb-130">Přidejte <xref:System.ServiceModel.XmlSerializerFormatAttribute> do kontraktu služby v souboru *reference.cs* v projektu klientské aplikace v části **serviceReference** -> **reference. svcmap**.</span><span class="sxs-lookup"><span data-stu-id="694fb-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="694fb-131">Všimněte si, že je třeba zobrazit všechny soubory v **Průzkumník řešení** pro zobrazení těchto souborů.</span><span class="sxs-lookup"><span data-stu-id="694fb-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3. <span data-ttu-id="694fb-132">Sestavte klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="694fb-132">Build the client app.</span></span>  
  
4. <span data-ttu-id="694fb-133">Pomocí [nástroje Svcutil. exe (ServiceModel Metadata Utility)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vytvořte předem vygenerovaný soubor *. cs* pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="694fb-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="694fb-134">Argument assemblyPath Určuje cestu k sestavení klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="694fb-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="694fb-135">Například:</span><span class="sxs-lookup"><span data-stu-id="694fb-135">Such as:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="694fb-136">Vygeneruje se soubor *WCFClient.XmlSerializers.dll.cs* .</span><span class="sxs-lookup"><span data-stu-id="694fb-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5. <span data-ttu-id="694fb-137">Zkompilujte předem vygenerované sestavení serializace.</span><span class="sxs-lookup"><span data-stu-id="694fb-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="694fb-138">V závislosti na příkladu v předchozím kroku by příkaz Compile byl následující:</span><span class="sxs-lookup"><span data-stu-id="694fb-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```console  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="694fb-139">Ujistěte se, že vygenerovaná *WCFClient. XmlSerializers. dll* je ve stejném adresáři jako klientská aplikace, která v tomto případě je *WCFClient. exe* .</span><span class="sxs-lookup"><span data-stu-id="694fb-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6. <span data-ttu-id="694fb-140">Spusťte aplikaci klienta obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="694fb-140">Run the client app as usual.</span></span> <span data-ttu-id="694fb-141">Použije se předem vygenerované sestavení serializace.</span><span class="sxs-lookup"><span data-stu-id="694fb-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="694fb-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="694fb-142">Example</span></span>  
 <span data-ttu-id="694fb-143">Následující příkaz generuje typy serializace pro `XmlSerializer` typy, které používají všechny kontrakty služby v sestavení.</span><span class="sxs-lookup"><span data-stu-id="694fb-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```console  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="694fb-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="694fb-144">See also</span></span>

- [<span data-ttu-id="694fb-145">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="694fb-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
