---
title: 'Postupy: Konfigurace komponent COM využívajících rozhraní .NET Framework pro aktivaci bez registrace'
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea62f7dc5c47f52f94567857427e7add929b8b1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336574"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="f0801-102">Postupy: Konfigurace komponent COM využívajících rozhraní .NET Framework pro aktivaci bez registrace</span><span class="sxs-lookup"><span data-stu-id="f0801-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="f0801-103">Bezregistrační aktivace komponent využívajících rozhraní .NET Framework je jenom o něco složitější než pro komponenty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="f0801-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="f0801-104">Instalace vyžaduje dva manifesty:</span><span class="sxs-lookup"><span data-stu-id="f0801-104">The setup requires two manifests:</span></span>  
  
-   <span data-ttu-id="f0801-105">Aplikace modelu COM musí mít aplikace manifest Win32 – vizuální styl k identifikaci spravované součásti.</span><span class="sxs-lookup"><span data-stu-id="f0801-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
-   <span data-ttu-id="f0801-106">Komponenty založené na platformě .NET musí mít manifestu součásti aktivace informace potřebné v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f0801-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="f0801-107">Toto téma popisuje, jak přidružit aplikaci; manifest aplikace manifest součásti přidružit komponentu; a vložení manifestu do komponenty v sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0801-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="f0801-108">Chcete-li vytvořit manifest aplikace</span><span class="sxs-lookup"><span data-stu-id="f0801-108">To create an application manifest</span></span>  
  
1. <span data-ttu-id="f0801-109">Pomocí editoru XML, vytvořit (nebo upravit) manifest aplikace vlastněné aplikací modelu COM, který je spolupráce s jedním nebo více spravovaných komponenty.</span><span class="sxs-lookup"><span data-stu-id="f0801-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="f0801-110">Vložte následující standardní hlavičku na začátek souboru:</span><span class="sxs-lookup"><span data-stu-id="f0801-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="f0801-111">Informace o manifestu prvky a jejich atributů najdete v tématu [manifesty aplikací](/windows/desktop/SbsCs/application-manifests).</span><span class="sxs-lookup"><span data-stu-id="f0801-111">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="f0801-112">Určete vlastníka manifest.</span><span class="sxs-lookup"><span data-stu-id="f0801-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="f0801-113">V následujícím příkladu `myComApp` verze 1 vlastníkem souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="f0801-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4. <span data-ttu-id="f0801-114">Identifikujte závislá sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0801-114">Identify dependent assemblies.</span></span> <span data-ttu-id="f0801-115">V následujícím příkladu `myComApp` závisí na `myManagedComp`.</span><span class="sxs-lookup"><span data-stu-id="f0801-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="x86"   
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myManagedComp"   
                        version="6.0.0.0"   
                        processorArchitecture="X86"   
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="f0801-116">Uložit a název souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="f0801-116">Save and name the manifest file.</span></span> <span data-ttu-id="f0801-117">Název manifestu aplikace je název sestavení spustitelného souboru a příponu .manifest.</span><span class="sxs-lookup"><span data-stu-id="f0801-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="f0801-118">Například je název souboru manifestu aplikace pro myComApp.exe myComApp.exe.manifest.</span><span class="sxs-lookup"><span data-stu-id="f0801-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="f0801-119">Manifest aplikace můžete nainstalovat ve stejném adresáři jako aplikace modelu COM.</span><span class="sxs-lookup"><span data-stu-id="f0801-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="f0801-120">Alternativně můžete přidat ho jako prostředek do souboru .exe vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="f0801-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="f0801-121">Další informace najdete další informace najdete v tématu [o sestavení vedle sebe](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="f0801-121">For additional information, For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="f0801-122">K vytvoření manifestu komponenty</span><span class="sxs-lookup"><span data-stu-id="f0801-122">To create a component manifest</span></span>  
  
1. <span data-ttu-id="f0801-123">Pomocí editoru XML, vytvoření manifestu komponenty k popisu spravovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0801-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="f0801-124">Vložte následující standardní hlavičku na začátek souboru:</span><span class="sxs-lookup"><span data-stu-id="f0801-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. <span data-ttu-id="f0801-125">Určete vlastníka souboru.</span><span class="sxs-lookup"><span data-stu-id="f0801-125">Identify the owner of the file.</span></span> <span data-ttu-id="f0801-126">`<assemblyIdentity>` Elementu `<dependentAssembly>` prvku v souboru manifestu aplikace musí odpovídat názvu v manifestu součásti.</span><span class="sxs-lookup"><span data-stu-id="f0801-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="f0801-127">V následujícím příkladu `myManagedComp` verzi 1.2.3.4 je vlastníkem souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="f0801-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4. <span data-ttu-id="f0801-128">Identifikujte jednotlivé třídy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0801-128">Identify each class in the assembly.</span></span> <span data-ttu-id="f0801-129">Použití `<clrClass>` element k jednoznačné identifikaci každé třídě spravované sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0801-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="f0801-130">Element, který je podřízený z `<assembly>` element, atributy jsou popsané v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="f0801-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="f0801-131">Atribut</span><span class="sxs-lookup"><span data-stu-id="f0801-131">Attribute</span></span>|<span data-ttu-id="f0801-132">Popis</span><span class="sxs-lookup"><span data-stu-id="f0801-132">Description</span></span>|<span data-ttu-id="f0801-133">Požadováno</span><span class="sxs-lookup"><span data-stu-id="f0801-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="f0801-134">Identifikátor, který určuje třídy, která má být aktivován.</span><span class="sxs-lookup"><span data-stu-id="f0801-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="f0801-135">Ano</span><span class="sxs-lookup"><span data-stu-id="f0801-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="f0801-136">Řetězec, který informuje uživatele o komponentě.</span><span class="sxs-lookup"><span data-stu-id="f0801-136">A string that informs the user about the component.</span></span> <span data-ttu-id="f0801-137">Výchozím nastavením je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="f0801-137">An empty string is the default.</span></span>|<span data-ttu-id="f0801-138">Ne</span><span class="sxs-lookup"><span data-stu-id="f0801-138">No</span></span>|  
    |`name`|<span data-ttu-id="f0801-139">Řetězec, který představuje spravovanou třídu.</span><span class="sxs-lookup"><span data-stu-id="f0801-139">A string that represents the managed class.</span></span>|<span data-ttu-id="f0801-140">Ano</span><span class="sxs-lookup"><span data-stu-id="f0801-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="f0801-141">Identifikátor, který má být použit pro aktivaci s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="f0801-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="f0801-142">Ne</span><span class="sxs-lookup"><span data-stu-id="f0801-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="f0801-143">Model COM vláken.</span><span class="sxs-lookup"><span data-stu-id="f0801-143">The COM threading model.</span></span> <span data-ttu-id="f0801-144">Výchozí hodnota je "I".</span><span class="sxs-lookup"><span data-stu-id="f0801-144">"Both" is the default value.</span></span>|<span data-ttu-id="f0801-145">Ne</span><span class="sxs-lookup"><span data-stu-id="f0801-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="f0801-146">Určuje verze společného jazyka runtime (CLR) používat.</span><span class="sxs-lookup"><span data-stu-id="f0801-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="f0801-147">Pokud tento atribut není zadán, a CLR dosud není načtený, komponenta načtena s nainstalovanou CLR před CLR verze 4.</span><span class="sxs-lookup"><span data-stu-id="f0801-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="f0801-148">Pokud zadáte v1.0.3705, v1.1.4322 nebo v2.0.50727, verze automaticky provede dopředné obnovení na nejnovější CLR verze před CLR verze 4 (obvykle v2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="f0801-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="f0801-149">Pokud je již načtena jiná verze modulu CLR a zadaná verze je možné načíst vedle sebe v procesu, je uvedena verze je načten. v opačném případě se používá načtené CLR.</span><span class="sxs-lookup"><span data-stu-id="f0801-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="f0801-150">Tato akce může způsobit chyby načítání.</span><span class="sxs-lookup"><span data-stu-id="f0801-150">This might cause a load failure.</span></span>|<span data-ttu-id="f0801-151">Ne</span><span class="sxs-lookup"><span data-stu-id="f0801-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="f0801-152">Identifikátor, který obsahuje typ informace o třídě knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="f0801-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="f0801-153">Ne</span><span class="sxs-lookup"><span data-stu-id="f0801-153">No</span></span>|  
  
     <span data-ttu-id="f0801-154">Všechny značky atributů jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="f0801-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="f0801-155">Můžete získat CLSID, ProgID, práce s vlákny modely a verze modulu runtime zobrazením exportované knihovny typů pro sestavení ObjectViewer OLE/COM (Oleview.exe).</span><span class="sxs-lookup"><span data-stu-id="f0801-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="f0801-156">Následující komponenty manifest identifikuje dvě třídy `testClass1` a `testClass2`.</span><span class="sxs-lookup"><span data-stu-id="f0801-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"   
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="f0801-157">Uložit a název souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="f0801-157">Save and name the manifest file.</span></span> <span data-ttu-id="f0801-158">Název manifestu součásti je název sestavení knihovny následovaný příponou .manifest.</span><span class="sxs-lookup"><span data-stu-id="f0801-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="f0801-159">Například myManagedComp.dll je myManagedComp.manifest.</span><span class="sxs-lookup"><span data-stu-id="f0801-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="f0801-160">Manifest součásti musí vložen jako prostředek v sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0801-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="f0801-161">Pro vložení manifestu komponenty spravovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="f0801-161">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="f0801-162">Vytvořte skript prostředků, který obsahuje následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f0801-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="f0801-163">V tomto prohlášení `myManagedComp.manifest` je název manifestu komponenty jsou vložené.</span><span class="sxs-lookup"><span data-stu-id="f0801-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="f0801-164">V tomto příkladu je název souboru skriptu `myresource.rc`.</span><span class="sxs-lookup"><span data-stu-id="f0801-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="f0801-165">Kompilace skriptu s použitím Microsoft Windows Resource Compiler (Rc.exe).</span><span class="sxs-lookup"><span data-stu-id="f0801-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="f0801-166">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f0801-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="f0801-167">Vytvoří RC.exe `myresource.res` souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="f0801-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="f0801-168">Znovu zkompilovat sestavení zdrojového souboru a zadejte soubor prostředků pomocí **/win32res** možnost:</span><span class="sxs-lookup"><span data-stu-id="f0801-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     <span data-ttu-id="f0801-169">Opět `myresource.res` je název souboru prostředku, který obsahuje integrovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="f0801-169">Again, `myresource.res` is the name of the resource file containing embedded resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0801-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0801-170">See also</span></span>

- [<span data-ttu-id="f0801-171">Bezregistrační zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="f0801-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="f0801-172">[Požadavky pro zprostředkovatele komunikace s objekty COM bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f0801-172">[Requirements for Registration-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="f0801-173">[Konfigurace komponent COM pro aktivaci bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f0801-173">[Configuring COM Components for Registration-Free Activation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="f0801-174">[Bezregistrační aktivace. Na základě NET součásti: Názorný postup](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="f0801-174">[Registration-Free Activation of .NET-Based Components: A Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
