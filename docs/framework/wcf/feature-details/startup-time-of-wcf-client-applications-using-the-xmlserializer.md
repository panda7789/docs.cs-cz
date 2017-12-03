---
title: "Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 14f5cf25bbcde4732162f2c44c83661a0ac739ea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="b48e2-102">Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="b48e2-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="b48e2-103">Služby a klientské aplikace používající typy dat, které jsou serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilace kódu serializace pro tyto typy dat za běhu, což může vést k pomalé spuštění výkonu.</span><span class="sxs-lookup"><span data-stu-id="b48e2-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b48e2-104">Předem vygenerovaná serializace kódu je možné pouze v klientských aplikacích a není v služby.</span><span class="sxs-lookup"><span data-stu-id="b48e2-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="b48e2-105">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lze vylepšit výkon spuštění pro tyto aplikace generování kódu nezbytné serializace z kompilované sestavení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b48e2-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="b48e2-106">Svcutil.exe generuje kód serializace pro všechny typy dat používané v kontraktech služby v sestavení kompilované aplikace, které lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b48e2-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="b48e2-107">Služby a operace kontrakty, které používají <xref:System.Xml.Serialization.XmlSerializer> jsou označené <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b48e2-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="b48e2-108">Generování kódu serializace třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="b48e2-108">To generate XmlSerializer serialization code</span></span>  
  
1.  <span data-ttu-id="b48e2-109">Kompilaci kódu služba nebo klienta do jednoho nebo více sestavení.</span><span class="sxs-lookup"><span data-stu-id="b48e2-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2.  <span data-ttu-id="b48e2-110">Otevřete příkazový řádek SDK.</span><span class="sxs-lookup"><span data-stu-id="b48e2-110">Open an SDK command prompt.</span></span>  
  
3.  <span data-ttu-id="b48e2-111">Na příkazovém řádku spusťte nástroje Svcutil.exe v následujícím formátu.</span><span class="sxs-lookup"><span data-stu-id="b48e2-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="b48e2-112">`assemblyPath` Argument určuje cestu k sestavení, který obsahuje typy kontraktů služby.</span><span class="sxs-lookup"><span data-stu-id="b48e2-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="b48e2-113">Svcutil.exe generuje kód serializace pro všechny typy dat používané v kontraktech služby v sestavení kompilované aplikace, které lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b48e2-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="b48e2-114">Svcutil.exe mohou generovat jenom serializace kód C#.</span><span class="sxs-lookup"><span data-stu-id="b48e2-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="b48e2-115">Jeden souboru zdrojového kódu se generuje pro každý vstupní sestavení.</span><span class="sxs-lookup"><span data-stu-id="b48e2-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="b48e2-116">Nelze použít **/language** přepínač tak, aby změnit jazyk generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="b48e2-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="b48e2-117">Pokud chcete zadat cestu k závislá sestavení, použijte **/reference** možnost.</span><span class="sxs-lookup"><span data-stu-id="b48e2-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4.  <span data-ttu-id="b48e2-118">Kód vygenerovaný serializace zpřístupnit do vaší aplikace pomocí jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="b48e2-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1.  <span data-ttu-id="b48e2-119">Zkompilovat kód vygenerovaný serializace do samostatné sestavení s názvem [*původní sestavení*]. XmlSerializers.dll (například MyApp.XmlSerializers.dll).</span><span class="sxs-lookup"><span data-stu-id="b48e2-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="b48e2-120">Aplikace musí být schopen načíst sestavení, které musí být podepsané stejným klíčem jako původní sestavení.</span><span class="sxs-lookup"><span data-stu-id="b48e2-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="b48e2-121">Pokud jste znovu zkompiluje původní sestavení, je třeba znovu vygenerovat sestavení serializace.</span><span class="sxs-lookup"><span data-stu-id="b48e2-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2.  <span data-ttu-id="b48e2-122">Zkompilovat kód vygenerovaný serializace do samostatné sestavení a použít <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> na kontrakt služby, který používá <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b48e2-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="b48e2-123">Nastavte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> nebo <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> vlastnosti tak, aby odkazoval na sestavení kompilované serializace.</span><span class="sxs-lookup"><span data-stu-id="b48e2-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3.  <span data-ttu-id="b48e2-124">Kód vygenerovaný serializace kompilována sestavení vaší aplikace a přidat <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> servisní smlouvou, který používá <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b48e2-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="b48e2-125">Nenastavujte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> nebo <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b48e2-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="b48e2-126">Výchozí serializace sestavení se předpokládá, že se aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="b48e2-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="b48e2-127">Ke generování XmlSerializer serializace kódu v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b48e2-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1.  <span data-ttu-id="b48e2-128">Vytvoření klienta a služby WCF projekty v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b48e2-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="b48e2-129">Potom přidáte odkaz na službu do projektu klienta.</span><span class="sxs-lookup"><span data-stu-id="b48e2-129">Then, add a service reference to the client project.</span></span>  
  
2.  <span data-ttu-id="b48e2-130">Přidat <xref:System.ServiceModel.XmlSerializerFormatAttribute> servisní smlouvou v *reference.cs* souboru v projekt klientské aplikace za **serviceReference** -> **reference.svcmap** .</span><span class="sxs-lookup"><span data-stu-id="b48e2-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="b48e2-131">Všimněte si, že potřebujete zobrazit všechny soubory v **Průzkumníku řešení** zobrazíte tyto soubory.</span><span class="sxs-lookup"><span data-stu-id="b48e2-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3.  <span data-ttu-id="b48e2-132">Sestavení klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="b48e2-132">Build the client app.</span></span>  
  
4.  <span data-ttu-id="b48e2-133">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření předem vygenerovaných serializátoru *.cs* souboru pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="b48e2-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="b48e2-134">AssemblyPath argument určuje cestu k sestavení klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="b48e2-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="b48e2-135">Například:</span><span class="sxs-lookup"><span data-stu-id="b48e2-135">Such as:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="b48e2-136">*WCFClient.XmlSerializers.dll.cs* soubor bude vytvořen.</span><span class="sxs-lookup"><span data-stu-id="b48e2-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5.  <span data-ttu-id="b48e2-137">Kompilace sestavení předem vygenerovaná serializace.</span><span class="sxs-lookup"><span data-stu-id="b48e2-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="b48e2-138">Založena na příkladu v předchozím kroku, příkaz compile by být následující:</span><span class="sxs-lookup"><span data-stu-id="b48e2-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="b48e2-139">Zajistěte, aby vygenerovaného *WCFClient.XmlSerializers.dll* je ve stejném adresáři jako klientskou aplikaci, která je *WCFClient.exe* v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="b48e2-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6.  <span data-ttu-id="b48e2-140">Spusťte klientskou aplikaci jako obvykle.</span><span class="sxs-lookup"><span data-stu-id="b48e2-140">Run the client app as usual.</span></span> <span data-ttu-id="b48e2-141">Sestavení předem vygenerovaná serializace se použije.</span><span class="sxs-lookup"><span data-stu-id="b48e2-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b48e2-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="b48e2-142">Example</span></span>  
 <span data-ttu-id="b48e2-143">Následující příkaz vytvoří typy serializace pro `XmlSerializer` typy, které jakoukoli službu, měnící používán sestavení.</span><span class="sxs-lookup"><span data-stu-id="b48e2-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="b48e2-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="b48e2-144">See Also</span></span>  
 [<span data-ttu-id="b48e2-145">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="b48e2-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
