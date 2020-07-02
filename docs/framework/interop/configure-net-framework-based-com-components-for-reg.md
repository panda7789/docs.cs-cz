---
title: 'Postupy: Konfigurace komponent COM využívajících rozhraní .NET Framework pro aktivaci bez registrace'
description: Konfigurace. SÍŤOVÉ komponenty modelu COM pro aktivaci bez registrace. Instalační program vyžaduje manifest aplikace ve stylu Win32 a manifest součásti .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: 5263e042bafdb886b313f05751c29de0f5715211
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622195"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="aa235-104">Postupy: Konfigurace komponent COM využívajících rozhraní .NET Framework pro aktivaci bez registrace</span><span class="sxs-lookup"><span data-stu-id="aa235-104">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="aa235-105">Aktivace bez registrace pro komponenty založené na .NET Framework je poněkud složitější než pro součásti modelu COM.</span><span class="sxs-lookup"><span data-stu-id="aa235-105">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="aa235-106">Instalační program vyžaduje dva manifesty:</span><span class="sxs-lookup"><span data-stu-id="aa235-106">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="aa235-107">Aby bylo možné identifikovat spravovanou součást, musí mít aplikace modelu COM manifest aplikace ve stylu Win32.</span><span class="sxs-lookup"><span data-stu-id="aa235-107">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="aa235-108">Komponenty založené na .NET Framework musí mít manifest součásti pro informace o aktivaci potřebné v době běhu.</span><span class="sxs-lookup"><span data-stu-id="aa235-108">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="aa235-109">Toto téma popisuje, jak přidružit manifest aplikace k aplikaci. Přidružte manifest součásti k komponentě. a vložte manifest součásti do sestavení.</span><span class="sxs-lookup"><span data-stu-id="aa235-109">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
## <a name="create-an-application-manifest"></a><span data-ttu-id="aa235-110">Vytvoření manifestu aplikace</span><span class="sxs-lookup"><span data-stu-id="aa235-110">Create an application manifest</span></span>  
  
1. <span data-ttu-id="aa235-111">Pomocí editoru XML vytvořte (nebo upravte) manifest aplikace vlastněný aplikací modelu COM, která je v provozu s jednou nebo více spravovanými komponentami.</span><span class="sxs-lookup"><span data-stu-id="aa235-111">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="aa235-112">Vložte následující standardní hlavičku na začátek souboru:</span><span class="sxs-lookup"><span data-stu-id="aa235-112">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     <span data-ttu-id="aa235-113">Informace o prvcích manifestu a jejich atributech naleznete v tématu [manifesty aplikací](/windows/desktop/SbsCs/application-manifests).</span><span class="sxs-lookup"><span data-stu-id="aa235-113">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="aa235-114">Identifikujte vlastníka manifestu.</span><span class="sxs-lookup"><span data-stu-id="aa235-114">Identify the owner of the manifest.</span></span> <span data-ttu-id="aa235-115">V následujícím příkladu `myComApp` verze 1 vlastní soubor manifestu.</span><span class="sxs-lookup"><span data-stu-id="aa235-115">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />
    </assembly>  
    ```  
  
4. <span data-ttu-id="aa235-116">Identifikujte závislá sestavení.</span><span class="sxs-lookup"><span data-stu-id="aa235-116">Identify dependent assemblies.</span></span> <span data-ttu-id="aa235-117">V následujícím příkladu `myComApp` závisí na `myManagedComp` .</span><span class="sxs-lookup"><span data-stu-id="aa235-117">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
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
  
5. <span data-ttu-id="aa235-118">Uložte a pojmenujte soubor manifestu.</span><span class="sxs-lookup"><span data-stu-id="aa235-118">Save and name the manifest file.</span></span> <span data-ttu-id="aa235-119">Název manifestu aplikace je název spustitelného souboru sestavení následovaný příponou. manifest.</span><span class="sxs-lookup"><span data-stu-id="aa235-119">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="aa235-120">Například název souboru manifestu aplikace pro myComApp.exe je myComApp.exe. manifest.</span><span class="sxs-lookup"><span data-stu-id="aa235-120">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
<span data-ttu-id="aa235-121">Manifest aplikace můžete nainstalovat do stejného adresáře jako aplikace modelu COM.</span><span class="sxs-lookup"><span data-stu-id="aa235-121">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="aa235-122">Případně ho můžete přidat jako prostředek do souboru. exe aplikace.</span><span class="sxs-lookup"><span data-stu-id="aa235-122">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="aa235-123">Další informace najdete v tématu [o souběžných sestaveních](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="aa235-123">For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
## <a name="create-a-component-manifest"></a><span data-ttu-id="aa235-124">Vytvořit manifest součásti</span><span class="sxs-lookup"><span data-stu-id="aa235-124">Create a component manifest</span></span>  
  
1. <span data-ttu-id="aa235-125">Pomocí editoru XML vytvořte manifest součásti pro popis spravovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="aa235-125">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="aa235-126">Vložte následující standardní hlavičku na začátek souboru:</span><span class="sxs-lookup"><span data-stu-id="aa235-126">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. <span data-ttu-id="aa235-127">Identifikujte vlastníka souboru.</span><span class="sxs-lookup"><span data-stu-id="aa235-127">Identify the owner of the file.</span></span> <span data-ttu-id="aa235-128">`<assemblyIdentity>`Element `<dependentAssembly>` elementu v souboru manifestu aplikace se musí shodovat s prvkem v manifestu součásti.</span><span class="sxs-lookup"><span data-stu-id="aa235-128">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="aa235-129">V následujícím příkladu je `myManagedComp` verze 1.2.3.4 vlastníkem souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="aa235-129">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />
    </assembly>
    ```  
  
4. <span data-ttu-id="aa235-130">Identifikujte každou třídu v sestavení.</span><span class="sxs-lookup"><span data-stu-id="aa235-130">Identify each class in the assembly.</span></span> <span data-ttu-id="aa235-131">Pomocí `<clrClass>` elementu jednoznačně Identifikujte jednotlivé třídy ve spravovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="aa235-131">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="aa235-132">Element, který je dílčím prvkem `<assembly>` elementu, má atributy popsané v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="aa235-132">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="aa235-133">Atribut</span><span class="sxs-lookup"><span data-stu-id="aa235-133">Attribute</span></span>|<span data-ttu-id="aa235-134">Popis</span><span class="sxs-lookup"><span data-stu-id="aa235-134">Description</span></span>|<span data-ttu-id="aa235-135">Vyžadováno</span><span class="sxs-lookup"><span data-stu-id="aa235-135">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="aa235-136">Identifikátor, který určuje třídu, která má být aktivována.</span><span class="sxs-lookup"><span data-stu-id="aa235-136">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="aa235-137">Ano</span><span class="sxs-lookup"><span data-stu-id="aa235-137">Yes</span></span>|  
    |`description`|<span data-ttu-id="aa235-138">Řetězec, který informuje uživatele o komponentě.</span><span class="sxs-lookup"><span data-stu-id="aa235-138">A string that informs the user about the component.</span></span> <span data-ttu-id="aa235-139">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="aa235-139">An empty string is the default.</span></span>|<span data-ttu-id="aa235-140">Ne</span><span class="sxs-lookup"><span data-stu-id="aa235-140">No</span></span>|  
    |`name`|<span data-ttu-id="aa235-141">Řetězec, který představuje spravovanou třídu.</span><span class="sxs-lookup"><span data-stu-id="aa235-141">A string that represents the managed class.</span></span>|<span data-ttu-id="aa235-142">Ano</span><span class="sxs-lookup"><span data-stu-id="aa235-142">Yes</span></span>|  
    |`progid`|<span data-ttu-id="aa235-143">Identifikátor, který se má použít pro aktivaci s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="aa235-143">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="aa235-144">Ne</span><span class="sxs-lookup"><span data-stu-id="aa235-144">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="aa235-145">Model vláken modelu COM.</span><span class="sxs-lookup"><span data-stu-id="aa235-145">The COM threading model.</span></span> <span data-ttu-id="aa235-146">Výchozí hodnota je "obojí".</span><span class="sxs-lookup"><span data-stu-id="aa235-146">"Both" is the default value.</span></span>|<span data-ttu-id="aa235-147">Ne</span><span class="sxs-lookup"><span data-stu-id="aa235-147">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="aa235-148">Určuje verzi modulu CLR (Common Language Runtime), která se má použít.</span><span class="sxs-lookup"><span data-stu-id="aa235-148">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="aa235-149">Pokud tento atribut nezadáte a CLR již není načten, komponenta je načtena s nejnovějším nainstalovaným modulem CLR před modulem CLR verze 4.</span><span class="sxs-lookup"><span data-stu-id="aa235-149">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="aa235-150">Pokud zadáte v 1.0.3705, v 1.1.4322 nebo v 2.0.50727, verze se automaticky vrátí k nejnovější nainstalované verzi CLR před CLR verze 4 (obvykle v 2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="aa235-150">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="aa235-151">Pokud je již načtena jiná verze modulu CLR a zadaná verze může být načtena souběžně v rámci procesu, je načtena zadaná verze; v opačném případě je použit načtený modul CLR.</span><span class="sxs-lookup"><span data-stu-id="aa235-151">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="aa235-152">To může způsobit selhání načtení.</span><span class="sxs-lookup"><span data-stu-id="aa235-152">This might cause a load failure.</span></span>|<span data-ttu-id="aa235-153">Ne</span><span class="sxs-lookup"><span data-stu-id="aa235-153">No</span></span>|  
    |`tlbid`|<span data-ttu-id="aa235-154">Identifikátor knihovny typů, která obsahuje informace o typu třídy.</span><span class="sxs-lookup"><span data-stu-id="aa235-154">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="aa235-155">Ne</span><span class="sxs-lookup"><span data-stu-id="aa235-155">No</span></span>|  
  
     <span data-ttu-id="aa235-156">U všech značek atributů se rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="aa235-156">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="aa235-157">Identifikátory CLSID, ProgID, modely vláken a verzi modulu runtime lze získat zobrazením exportované knihovny typů pro sestavení pomocí technologie OLE/COM ObjectViewer (Oleview.exe).</span><span class="sxs-lookup"><span data-stu-id="aa235-157">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="aa235-158">Následující manifest komponenty identifikuje dvě třídy, `testClass1` a `testClass2` .</span><span class="sxs-lookup"><span data-stu-id="aa235-158">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
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
  
5. <span data-ttu-id="aa235-159">Uložte a pojmenujte soubor manifestu.</span><span class="sxs-lookup"><span data-stu-id="aa235-159">Save and name the manifest file.</span></span> <span data-ttu-id="aa235-160">Název manifestu součásti je název knihovny sestavení následovaný příponou. manifest.</span><span class="sxs-lookup"><span data-stu-id="aa235-160">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="aa235-161">Například myManagedComp.dll je myManagedComp. manifest.</span><span class="sxs-lookup"><span data-stu-id="aa235-161">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="aa235-162">Manifest součásti je nutné vložit jako prostředek v sestavení.</span><span class="sxs-lookup"><span data-stu-id="aa235-162">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="aa235-163">Vložení manifestu součásti do spravovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="aa235-163">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="aa235-164">Vytvořte skript prostředků, který obsahuje následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="aa235-164">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="aa235-165">V tomto příkazu `myManagedComp.manifest` je název manifestu součásti, který se má vložit.</span><span class="sxs-lookup"><span data-stu-id="aa235-165">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="aa235-166">V tomto příkladu je název souboru skriptu `myresource.rc` .</span><span class="sxs-lookup"><span data-stu-id="aa235-166">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="aa235-167">Zkompilujte skript pomocí kompilátoru prostředků Microsoft Windows (Rc.exe).</span><span class="sxs-lookup"><span data-stu-id="aa235-167">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="aa235-168">Do příkazového řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="aa235-168">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="aa235-169">Rc.exe vytvoří `myresource.res` soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="aa235-169">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="aa235-170">Zkompilujte zdrojový soubor sestavení znovu a zadejte soubor prostředků pomocí možnosti **parametr/win32res** :</span><span class="sxs-lookup"><span data-stu-id="aa235-170">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="aa235-171">Znovu `myresource.res` je název souboru prostředků obsahujícího vložené prostředky.</span><span class="sxs-lookup"><span data-stu-id="aa235-171">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa235-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa235-172">See also</span></span>

- [<span data-ttu-id="aa235-173">Zprostředkovatel komunikace s objekty COM bez registrace</span><span class="sxs-lookup"><span data-stu-id="aa235-173">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="aa235-174">[Požadavky na zprostředkovatele komunikace s objekty COM bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="aa235-174">[Requirements for Registration-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="aa235-175">[Konfigurace komponent modelu COM pro aktivaci bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="aa235-175">[Configuring COM Components for Registration-Free Activation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="aa235-176">[Aktivace aplikace bez registrace. Komponenty založené na síti: Návod](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="aa235-176">[Registration-Free Activation of .NET-Based Components: A Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
