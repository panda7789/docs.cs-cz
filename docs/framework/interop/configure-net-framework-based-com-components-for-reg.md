---
title: 'Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework'
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: 9e273bd3e4bf2bb6945fe48c850783a54fa9a869
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291757"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="0a397-102">Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0a397-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="0a397-103">Aktivace bez registrace pro komponenty založené na .NET Framework je poněkud složitější než pro součásti modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0a397-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="0a397-104">Instalační program vyžaduje dva manifesty:</span><span class="sxs-lookup"><span data-stu-id="0a397-104">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="0a397-105">Aby bylo možné identifikovat spravovanou součást, musí mít aplikace modelu COM manifest aplikace ve stylu Win32.</span><span class="sxs-lookup"><span data-stu-id="0a397-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="0a397-106">Komponenty založené na .NET Framework musí mít manifest součásti pro informace o aktivaci potřebné v době běhu.</span><span class="sxs-lookup"><span data-stu-id="0a397-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="0a397-107">Toto téma popisuje, jak přidružit manifest aplikace k aplikaci. Přidružte manifest součásti k komponentě. a vložte manifest součásti do sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a397-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
## <a name="create-an-application-manifest"></a><span data-ttu-id="0a397-108">Vytvoření manifestu aplikace</span><span class="sxs-lookup"><span data-stu-id="0a397-108">Create an application manifest</span></span>  
  
1. <span data-ttu-id="0a397-109">Pomocí editoru XML vytvořte (nebo upravte) manifest aplikace vlastněný aplikací modelu COM, která je v provozu s jednou nebo více spravovanými komponentami.</span><span class="sxs-lookup"><span data-stu-id="0a397-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="0a397-110">Vložte následující standardní hlavičku na začátek souboru:</span><span class="sxs-lookup"><span data-stu-id="0a397-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     <span data-ttu-id="0a397-111">Informace o prvcích manifestu a jejich atributech naleznete v tématu [manifesty aplikací](/windows/desktop/SbsCs/application-manifests).</span><span class="sxs-lookup"><span data-stu-id="0a397-111">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="0a397-112">Identifikujte vlastníka manifestu.</span><span class="sxs-lookup"><span data-stu-id="0a397-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="0a397-113">V následujícím příkladu `myComApp` verze 1 vlastní soubor manifestu.</span><span class="sxs-lookup"><span data-stu-id="0a397-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
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
  
4. <span data-ttu-id="0a397-114">Identifikujte závislá sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a397-114">Identify dependent assemblies.</span></span> <span data-ttu-id="0a397-115">V následujícím příkladu `myComApp` závisí na `myManagedComp`.</span><span class="sxs-lookup"><span data-stu-id="0a397-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
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
  
5. <span data-ttu-id="0a397-116">Uložte a pojmenujte soubor manifestu.</span><span class="sxs-lookup"><span data-stu-id="0a397-116">Save and name the manifest file.</span></span> <span data-ttu-id="0a397-117">Název manifestu aplikace je název spustitelného souboru sestavení následovaný příponou. manifest.</span><span class="sxs-lookup"><span data-stu-id="0a397-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="0a397-118">Například název souboru manifestu aplikace pro myComApp. exe je myComApp. exe. manifest.</span><span class="sxs-lookup"><span data-stu-id="0a397-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
<span data-ttu-id="0a397-119">Manifest aplikace můžete nainstalovat do stejného adresáře jako aplikace modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0a397-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="0a397-120">Případně ho můžete přidat jako prostředek do souboru. exe aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a397-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="0a397-121">Další informace najdete v tématu [o souběžných sestaveních](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="0a397-121">For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
## <a name="create-a-component-manifest"></a><span data-ttu-id="0a397-122">Vytvořit manifest součásti</span><span class="sxs-lookup"><span data-stu-id="0a397-122">Create a component manifest</span></span>  
  
1. <span data-ttu-id="0a397-123">Pomocí editoru XML vytvořte manifest součásti pro popis spravovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a397-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="0a397-124">Vložte následující standardní hlavičku na začátek souboru:</span><span class="sxs-lookup"><span data-stu-id="0a397-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. <span data-ttu-id="0a397-125">Identifikujte vlastníka souboru.</span><span class="sxs-lookup"><span data-stu-id="0a397-125">Identify the owner of the file.</span></span> <span data-ttu-id="0a397-126">Element `<assemblyIdentity>` `<dependentAssembly>` elementu v souboru manifestu aplikace se musí shodovat s prvkem v manifestu součásti.</span><span class="sxs-lookup"><span data-stu-id="0a397-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="0a397-127">V následujícím příkladu je `myManagedComp` verze 1.2.3.4 vlastníkem souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="0a397-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
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
  
4. <span data-ttu-id="0a397-128">Identifikujte každou třídu v sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a397-128">Identify each class in the assembly.</span></span> <span data-ttu-id="0a397-129">Pomocí `<clrClass>` elementu jednoznačně Identifikujte jednotlivé třídy ve spravovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a397-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="0a397-130">Element, který je dílčím prvkem `<assembly>` elementu, má atributy popsané v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="0a397-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="0a397-131">Atribut</span><span class="sxs-lookup"><span data-stu-id="0a397-131">Attribute</span></span>|<span data-ttu-id="0a397-132">Popis</span><span class="sxs-lookup"><span data-stu-id="0a397-132">Description</span></span>|<span data-ttu-id="0a397-133">Požaduje se</span><span class="sxs-lookup"><span data-stu-id="0a397-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="0a397-134">Identifikátor, který určuje třídu, která má být aktivována.</span><span class="sxs-lookup"><span data-stu-id="0a397-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="0a397-135">Ano</span><span class="sxs-lookup"><span data-stu-id="0a397-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="0a397-136">Řetězec, který informuje uživatele o komponentě.</span><span class="sxs-lookup"><span data-stu-id="0a397-136">A string that informs the user about the component.</span></span> <span data-ttu-id="0a397-137">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="0a397-137">An empty string is the default.</span></span>|<span data-ttu-id="0a397-138">Ne</span><span class="sxs-lookup"><span data-stu-id="0a397-138">No</span></span>|  
    |`name`|<span data-ttu-id="0a397-139">Řetězec, který představuje spravovanou třídu.</span><span class="sxs-lookup"><span data-stu-id="0a397-139">A string that represents the managed class.</span></span>|<span data-ttu-id="0a397-140">Ano</span><span class="sxs-lookup"><span data-stu-id="0a397-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="0a397-141">Identifikátor, který se má použít pro aktivaci s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="0a397-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="0a397-142">Ne</span><span class="sxs-lookup"><span data-stu-id="0a397-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="0a397-143">Model vláken modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0a397-143">The COM threading model.</span></span> <span data-ttu-id="0a397-144">Výchozí hodnota je "obojí".</span><span class="sxs-lookup"><span data-stu-id="0a397-144">"Both" is the default value.</span></span>|<span data-ttu-id="0a397-145">Ne</span><span class="sxs-lookup"><span data-stu-id="0a397-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="0a397-146">Určuje verzi modulu CLR (Common Language Runtime), která se má použít.</span><span class="sxs-lookup"><span data-stu-id="0a397-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="0a397-147">Pokud tento atribut nezadáte a CLR již není načten, komponenta je načtena s nejnovějším nainstalovaným modulem CLR před modulem CLR verze 4.</span><span class="sxs-lookup"><span data-stu-id="0a397-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="0a397-148">Pokud zadáte v 1.0.3705, v 1.1.4322 nebo v 2.0.50727, verze se automaticky vrátí k nejnovější nainstalované verzi CLR před CLR verze 4 (obvykle v 2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="0a397-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="0a397-149">Pokud je již načtena jiná verze modulu CLR a zadaná verze může být načtena souběžně v rámci procesu, je načtena zadaná verze; v opačném případě je použit načtený modul CLR.</span><span class="sxs-lookup"><span data-stu-id="0a397-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="0a397-150">To může způsobit selhání načtení.</span><span class="sxs-lookup"><span data-stu-id="0a397-150">This might cause a load failure.</span></span>|<span data-ttu-id="0a397-151">Ne</span><span class="sxs-lookup"><span data-stu-id="0a397-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="0a397-152">Identifikátor knihovny typů, která obsahuje informace o typu třídy.</span><span class="sxs-lookup"><span data-stu-id="0a397-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="0a397-153">Ne</span><span class="sxs-lookup"><span data-stu-id="0a397-153">No</span></span>|  
  
     <span data-ttu-id="0a397-154">U všech značek atributů se rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="0a397-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="0a397-155">Identifikátory CLSID, ProgID, modely vláken a verze modulu runtime lze získat zobrazením exportované knihovny typů pro sestavení pomocí technologie OLE/COM ObjectViewer (Oleview. exe).</span><span class="sxs-lookup"><span data-stu-id="0a397-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="0a397-156">Následující manifest komponenty identifikuje dvě třídy, `testClass1` a. `testClass2`</span><span class="sxs-lookup"><span data-stu-id="0a397-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
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
  
5. <span data-ttu-id="0a397-157">Uložte a pojmenujte soubor manifestu.</span><span class="sxs-lookup"><span data-stu-id="0a397-157">Save and name the manifest file.</span></span> <span data-ttu-id="0a397-158">Název manifestu součásti je název knihovny sestavení následovaný příponou. manifest.</span><span class="sxs-lookup"><span data-stu-id="0a397-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="0a397-159">Například myManagedComp. dll je myManagedComp. manifest.</span><span class="sxs-lookup"><span data-stu-id="0a397-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="0a397-160">Manifest součásti je nutné vložit jako prostředek v sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a397-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="0a397-161">Vložení manifestu součásti do spravovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="0a397-161">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="0a397-162">Vytvořte skript prostředků, který obsahuje následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="0a397-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="0a397-163">V tomto příkazu je `myManagedComp.manifest` název manifestu součásti, který se má vložit.</span><span class="sxs-lookup"><span data-stu-id="0a397-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="0a397-164">V tomto příkladu je `myresource.rc`název souboru skriptu.</span><span class="sxs-lookup"><span data-stu-id="0a397-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="0a397-165">Zkompilujte skript pomocí kompilátoru prostředků Microsoft Windows (RC. exe).</span><span class="sxs-lookup"><span data-stu-id="0a397-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="0a397-166">Do příkazového řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="0a397-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="0a397-167">RC. exe vytvoří soubor `myresource.res` prostředků.</span><span class="sxs-lookup"><span data-stu-id="0a397-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="0a397-168">Zkompilujte zdrojový soubor sestavení znovu a zadejte soubor prostředků pomocí možnosti **parametr/win32res** :</span><span class="sxs-lookup"><span data-stu-id="0a397-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="0a397-169">Znovu `myresource.res` je název souboru prostředků obsahujícího vložené prostředky.</span><span class="sxs-lookup"><span data-stu-id="0a397-169">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a397-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a397-170">See also</span></span>

- [<span data-ttu-id="0a397-171">Bezregistrační zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="0a397-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="0a397-172">[Požadavky na zprostředkovatele komunikace s objekty COM bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0a397-172">[Requirements for Registration-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="0a397-173">[Konfigurace komponent modelu COM pro aktivaci bez registrace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0a397-173">[Configuring COM Components for Registration-Free Activation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="0a397-174">[Aktivace aplikace bez registrace. Komponenty založené na síti: Návod](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="0a397-174">[Registration-Free Activation of .NET-Based Components: A Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
