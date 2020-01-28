---
title: 'Postupy: registrace a konfigurace monikeru služby'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: fc0b2d00bcc8e3b14c491446f16297c1036b783b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747087"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="c53f9-102">Postupy: registrace a konfigurace monikeru služby</span><span class="sxs-lookup"><span data-stu-id="c53f9-102">How to: Register and Configure a Service Moniker</span></span>

<span data-ttu-id="c53f9-103">Předtím, než použijete moniker služby Windows Communication Foundation (WCF) v rámci aplikace modelu COM se zadaným kontraktem, je nutné zaregistrovat požadované typy s atributem COM a nakonfigurovat aplikaci COM a moniker s požadovanou vazbou. rozšířeného.</span><span class="sxs-lookup"><span data-stu-id="c53f9-103">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>

## <a name="register-the-required-attributed-types-with-com"></a><span data-ttu-id="c53f9-104">Registrace požadovaných typů s atributy pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="c53f9-104">Register the required attributed types with COM</span></span>

1. <span data-ttu-id="c53f9-105">Pomocí nástroje [Svcutil. exe (ServiceModel Metadata Utility)](../servicemodel-metadata-utility-tool-svcutil-exe.md) načtěte kontrakt metadat ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="c53f9-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="c53f9-106">Tím se vygeneruje zdrojový kód pro sestavení klienta WCF a konfigurační soubor klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="c53f9-106">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>

2. <span data-ttu-id="c53f9-107">Zajistěte, aby byly typy v sestavení označeny jako `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="c53f9-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="c53f9-108">Chcete-li to provést, přidejte následující atribut do souboru *AssemblyInfo.cs* v projektu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c53f9-108">To do so, add the following attribute to the *AssemblyInfo.cs* file in your Visual Studio project.</span></span>

    ```csharp
    [assembly: ComVisible(true)]
    ```

3. <span data-ttu-id="c53f9-109">Zkompilujte spravovaný klient služby WCF jako sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="c53f9-109">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="c53f9-110">To vyžaduje podepisování pomocí páru kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="c53f9-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="c53f9-111">Další informace naleznete v tématu [podepisování sestavení silným názvem](../../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="c53f9-111">For more information, see [Signing an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>

4. <span data-ttu-id="c53f9-112">Použijte nástroj registrace sestavení (Regasm. exe) s možností `-tlb` k registraci typů v sestavení pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c53f9-112">Use the Assembly Registration (Regasm.exe) tool with the `-tlb` option to register the types in the assembly with COM.</span></span>

5. <span data-ttu-id="c53f9-113">K přidání sestavení do globální mezipaměti sestavení (GAC) použijte nástroj Global Assembly Cache (Gacutil. exe).</span><span class="sxs-lookup"><span data-stu-id="c53f9-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c53f9-114">Podpis sestavení a jeho přidání do globální mezipaměti sestavení (GAC) je volitelný postup, ale může zjednodušit proces načítání sestavení ze správného umístění za běhu.</span><span class="sxs-lookup"><span data-stu-id="c53f9-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>

## <a name="configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="c53f9-115">Konfigurace aplikace COM a monikeru s požadovanou konfigurací vazby</span><span class="sxs-lookup"><span data-stu-id="c53f9-115">Configure the COM application and the moniker with the required binding configuration</span></span>

- <span data-ttu-id="c53f9-116">Vložte definice vazeb (generované [nástrojem Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) do generovaného konfiguračního souboru klientské aplikace) v konfiguračním souboru klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="c53f9-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="c53f9-117">Například pro spustitelný soubor Visual Basic 6,0 s názvem CallCenterClient. exe by měla být konfigurace umístěna do souboru s názvem CallCenterConfig. exe. config v rámci stejného adresáře jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="c53f9-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="c53f9-118">Klientská aplikace může nyní použít moniker.</span><span class="sxs-lookup"><span data-stu-id="c53f9-118">The client application can now use the moniker.</span></span> <span data-ttu-id="c53f9-119">Všimněte si, že konfigurace vazby není vyžadována, pokud používáte jeden ze standardních typů vazby poskytovaných službou WCF.</span><span class="sxs-lookup"><span data-stu-id="c53f9-119">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>

     <span data-ttu-id="c53f9-120">Následující typ je zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="c53f9-120">The following type is registered.</span></span>

    ```csharp
    using System.ServiceModel;

    [ServiceContract]
    public interface IMathService
    {
        [OperationContract]
        public int Add(int x, int y);
        [OperationContract]
        public int Subtract(int x, int y);
    }
    ```

     <span data-ttu-id="c53f9-121">Aplikace je vystavena pomocí `wsHttpBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="c53f9-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="c53f9-122">Pro daný typ a konfiguraci aplikace jsou použity následující příklady řetězců monikeru.</span><span class="sxs-lookup"><span data-stu-id="c53f9-122">For the given type and application configuration, the following example moniker strings are used.</span></span>

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1
    ```

     <span data-ttu-id="c53f9-123">nebo</span><span class="sxs-lookup"><span data-stu-id="c53f9-123">or</span></span>

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}
    ```

     <span data-ttu-id="c53f9-124">Můžete použít kterýkoli z těchto řetězců monikeru z aplikace Visual Basic 6,0 po přidání odkazu na sestavení, které obsahuje `IMathService` typy, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c53f9-124">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>

    ```vb
    Dim mathProxy As IMathService
    Dim result As Integer

    Set mathProxy = GetObject( _
            "service4:address=http://localhost/MathService, _
            binding=wsHttpBinding, _
            bindingConfiguration=Binding1")

    result = mathProxy.Add(3, 5)
    ```

     <span data-ttu-id="c53f9-125">V tomto příkladu je definice pro konfiguraci vazby `Binding1` uložená v vhodně pojmenovaném konfiguračním souboru pro klientskou aplikaci, jako je *vb6appname. exe. config*.</span><span class="sxs-lookup"><span data-stu-id="c53f9-125">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as *vb6appname.exe.config*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c53f9-126">Můžete použít podobný kód v C#, C++nebo v jakékoli jiné aplikaci jazyka .NET.</span><span class="sxs-lookup"><span data-stu-id="c53f9-126">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c53f9-127">Pokud je moniker poškozený nebo pokud není služba k dispozici, volání `GetObject` vrátí chybu neplatné syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c53f9-127">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="c53f9-128">Pokud se zobrazí tato chyba, ujistěte se, že moniker, který používáte, je správný a služba je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c53f9-128">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>

     <span data-ttu-id="c53f9-129">I když se toto téma zaměřuje na použití monikeru služby z kódu Visual Basic 6,0, můžete použít moniker služby z jiných jazyků.</span><span class="sxs-lookup"><span data-stu-id="c53f9-129">Although this topic focuses on using the service moniker from Visual Basic 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="c53f9-130">Při použití monikeru z C++ kódu by se sestavení vygenerované pomocí Svcutil. exe mělo importovat s "no_namespace named_guids raw_interfaces_only", jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c53f9-130">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>

    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids
    ```

     <span data-ttu-id="c53f9-131">Tím se upraví importované definice rozhraní, aby všechny metody vracely `HResult`.</span><span class="sxs-lookup"><span data-stu-id="c53f9-131">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="c53f9-132">Jakékoli jiné návratové hodnoty jsou převedeny na výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="c53f9-132">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="c53f9-133">Celkové provedení metod zůstává stejné.</span><span class="sxs-lookup"><span data-stu-id="c53f9-133">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="c53f9-134">To umožňuje určit příčinu výjimky při volání metody na proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="c53f9-134">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="c53f9-135">Tato funkce je k dispozici C++ pouze z kódu.</span><span class="sxs-lookup"><span data-stu-id="c53f9-135">This functionality is only available from C++ code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c53f9-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c53f9-136">See also</span></span>

- [<span data-ttu-id="c53f9-137">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="c53f9-137">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
