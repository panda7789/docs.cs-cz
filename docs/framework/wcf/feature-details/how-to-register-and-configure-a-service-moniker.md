---
title: 'Postupy: registrace a konfigurace Monikeru služby'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 52b3ec27560ca2dc47b7951cb209f33f307fa7ea
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="cf37f-102">Postupy: registrace a konfigurace Monikeru služby</span><span class="sxs-lookup"><span data-stu-id="cf37f-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="cf37f-103">Před použitím [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] monikeru služby v rámci aplikace modelu COM s typem kontrakt, je nutné zaregistrovat požadované s atributy typy v modelu COM a nakonfigurovat aplikaci COM a moniker s konfigurací požadovaná vazba.</span><span class="sxs-lookup"><span data-stu-id="cf37f-103">Before using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="cf37f-104">Registrace vyžaduje s atributy typy v modelu COM</span><span class="sxs-lookup"><span data-stu-id="cf37f-104">To register the required attributed types with COM</span></span>  
  
1.  <span data-ttu-id="cf37f-105">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj k načtení metadat kontrakt z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="cf37f-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="cf37f-106">Tím se vygeneruje zdrojový kód [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sestavení klienta a klientské aplikace konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="cf37f-106">This generates the source code for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly and a client application configuration file.</span></span>  
  
2.  <span data-ttu-id="cf37f-107">Ujistěte se, že typy v sestavení jsou označeny jako `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="cf37f-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="cf37f-108">Uděláte to tak, přidejte následující atribut do souboru AssemblyInfo.cs v projektu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf37f-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  <span data-ttu-id="cf37f-109">Kompilace spravovaný [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta jako sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="cf37f-109">Compile the managed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as a strong-named assembly.</span></span> <span data-ttu-id="cf37f-110">To vyžaduje podepsání pomocí páru kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="cf37f-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="cf37f-111">Další informace najdete v tématu [podepsání sestavení se silným názvem](http://go.microsoft.com/fwlink/?LinkId=94874) v příručce pro vývojáře .NET.</span><span class="sxs-lookup"><span data-stu-id="cf37f-111">For more information, see [Signing an Assembly with a Strong Name](http://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4.  <span data-ttu-id="cf37f-112">Použijte nástroj Assembly Registration (Regasm.exe) s `/tlb` možnost zaregistrovat typy v sestavení s COM.</span><span class="sxs-lookup"><span data-stu-id="cf37f-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5.  <span data-ttu-id="cf37f-113">Použijte nástroj globální mezipaměti sestavení (Gacutil.exe) pro přidání sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="cf37f-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cf37f-114">Podepisování sestavení a její přidání do globální mezipaměti sestavení jsou volitelné kroky, ale jejich může zjednodušit proces načítání sestavení za běhu na správném místě.</span><span class="sxs-lookup"><span data-stu-id="cf37f-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="cf37f-115">Konfigurace aplikace modelu COM a Přezdívka s konfigurací požadovaná vazba</span><span class="sxs-lookup"><span data-stu-id="cf37f-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
-   <span data-ttu-id="cf37f-116">Umístěte definice vazba (vygenerované [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) v konfiguračním souboru aplikace generovaného klienta) v konfiguračním souboru aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="cf37f-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="cf37f-117">Například pro Visual Basic 6.0 spustitelný soubor s názvem CallCenterClient.exe, musí být umístěny konfiguraci do souboru s názvem CallCenterConfig.exe.config ve stejném adresáři jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="cf37f-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="cf37f-118">Klientská aplikace teď můžete použít přezdívka.</span><span class="sxs-lookup"><span data-stu-id="cf37f-118">The client application can now use the moniker.</span></span> <span data-ttu-id="cf37f-119">Všimněte si, že pokud pomocí jedné z standardní typy poskytované vazby není potřeba Konfigurace vazeb [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf37f-119">Note that the binding configuration is not required if using one of the standard binding types provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
     <span data-ttu-id="cf37f-120">Následující typ je registrován.</span><span class="sxs-lookup"><span data-stu-id="cf37f-120">The following type is registered.</span></span>  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     <span data-ttu-id="cf37f-121">Aplikace je vystaven pomocí `wsHttpBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="cf37f-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="cf37f-122">Pro daný typ a konfiguraci aplikace se používají následující příklad Přezdívka řetězce.</span><span class="sxs-lookup"><span data-stu-id="cf37f-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="cf37f-123">Můžete použít některý z těchto Přezdívka řetězců z v rámci aplikace Visual Basic 6.0, po přidání odkaz na sestavení, které obsahuje `IMathService` typů, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="cf37f-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="cf37f-124">V tomto příkladu definici konfigurace vazeb `Binding1` je uložen v vhodně pojmenované konfigurační soubor pro klientská aplikace, jako je například vb6appname.exe.config.</span><span class="sxs-lookup"><span data-stu-id="cf37f-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cf37f-125">Můžete podobný kódu v C#, jazyka C++ nebo jiné aplikace rozhraní .NET jazyka.</span><span class="sxs-lookup"><span data-stu-id="cf37f-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cf37f-126">: Pokud Přezdívka je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chybu "Neplatná syntaxe".</span><span class="sxs-lookup"><span data-stu-id="cf37f-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="cf37f-127">Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cf37f-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="cf37f-128">I když toto téma se zaměřuje na použití monikeru služby z kódu jazyka Visual Basic 6.0, je použití monikeru služby z jiných jazyků.</span><span class="sxs-lookup"><span data-stu-id="cf37f-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="cf37f-129">Když pomocí Přezdívka z jazyka C++ kódové Svcutil.exe generované sestavení by měly naimportovány s "named_guids – no_namespace – raw_interfaces_only –" jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="cf37f-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="cf37f-130">To definice importované rozhraní upraví tak, aby všechny metody vrátit `HResult`.</span><span class="sxs-lookup"><span data-stu-id="cf37f-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="cf37f-131">Všechny ostatní vrácené hodnoty se převedou na výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="cf37f-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="cf37f-132">Celkový provoz metody zůstává stejná.</span><span class="sxs-lookup"><span data-stu-id="cf37f-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="cf37f-133">To umožňuje určit, proč k výjimce při volání metody na proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="cf37f-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="cf37f-134">Tato funkce je dostupná pouze z kódu jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="cf37f-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf37f-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf37f-135">See Also</span></span>  
 [<span data-ttu-id="cf37f-136">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="cf37f-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
