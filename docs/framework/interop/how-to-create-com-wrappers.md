---
title: 'Postupy: Vytváření obálek COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4deb355a7b523437ae31a1d2b9c79e3b8d4f40a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="a51c7-102">Postupy: Vytváření obálek COM</span><span class="sxs-lookup"><span data-stu-id="a51c7-102">How to: Create COM Wrappers</span></span>
<span data-ttu-id="a51c7-103">Obálky modelu COM (Component Object) můžete vytvořit pomocí [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] funkce nebo rozhraní .NET Framework nástroje Tlbimp.exe a Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="a51c7-103">You can create Component Object Model (COM) wrappers by using [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="a51c7-104">Obě metody generovat dva typy COM – obálky:</span><span class="sxs-lookup"><span data-stu-id="a51c7-104">Both methods generate two types of COM wrappers:</span></span>  
  
-   <span data-ttu-id="a51c7-105">A [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) z knihovny typů ke spuštění objektu COM ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="a51c7-105">A [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>  
  
-   <span data-ttu-id="a51c7-106">A [obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md) s se požadovaná nastavení registru pro spuštění spravovaného objektu v nativní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a51c7-106">A [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>  
  
 <span data-ttu-id="a51c7-107">V [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], obálky COM můžete přidat jako odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="a51c7-107">In [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], you can add the COM wrapper as a reference to your project.</span></span>  
  
## <a name="wrapping-com-objects-in-a-managed-application"></a><span data-ttu-id="a51c7-108">Zabalení COM – objekty ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="a51c7-108">Wrapping COM Objects in a Managed Application</span></span>  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="a51c7-109">Chcete-li vytvořit obálka volatelná za běhu pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a51c7-109">To create a runtime callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="a51c7-110">Otevřete projekt pro spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="a51c7-110">Open the project for your managed application.</span></span>  
  
2.  <span data-ttu-id="a51c7-111">Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="a51c7-111">On the **Project** menu, click **Show All Files**.</span></span>  
  
3.  <span data-ttu-id="a51c7-112">Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="a51c7-112">On the **Project** menu, click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="a51c7-113">V dialogovém okně Přidat odkaz klepněte **COM** , vyberte součást, kterou chcete použít a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="a51c7-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>  
  
     <span data-ttu-id="a51c7-114">V **Průzkumníku**, Všimněte si, že komponenty modelu COM přidán do složky odkazů v projektu.</span><span class="sxs-lookup"><span data-stu-id="a51c7-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>  
  
 <span data-ttu-id="a51c7-115">Teď můžete napsat kód pro přístup k objektu COM.</span><span class="sxs-lookup"><span data-stu-id="a51c7-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="a51c7-116">Můžete začít tím, že deklarujete objekt, například s `Imports` příkaz pro [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nebo `Using` příkaz pro [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a51c7-116">You can begin by declaring the object, such as with an `Imports` statement for [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] or a `Using` statement for [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a51c7-117">Pokud chcete program komponenty aplikace Microsoft Office, nejprve nainstalujte [primární zprostředkovatel komunikace s objekty sestavení sady Microsoft Office](http://go.microsoft.com/fwlink/?LinkId=50479) (PIA) z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="a51c7-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](http://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="a51c7-118">V kroku 4, vyberte nejnovější verzi k dispozici pro produkt Office, jako například chcete objektu knihovny **Microsoft Word 11.0 objektu knihovny**.</span><span class="sxs-lookup"><span data-stu-id="a51c7-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="a51c7-119">Chcete-li vytvořit obálka volatelná za běhu pomocí rozhraní .NET Framework – nástroje</span><span class="sxs-lookup"><span data-stu-id="a51c7-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="a51c7-120">Spustit [Tlbimp.exe (Importér knihovny)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="a51c7-120">Run the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="a51c7-121">Tento nástroj vytvoří sestavení obsahující metadat v době běhu pro typy definované v původní knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="a51c7-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrapping-managed-objects-in-a-native-application"></a><span data-ttu-id="a51c7-122">Zabalení spravované objekty v nativní aplikace</span><span class="sxs-lookup"><span data-stu-id="a51c7-122">Wrapping Managed Objects in a Native Application</span></span>  
  
#### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="a51c7-123">Chcete-li vytvořit obálka volatelná aplikacemi COM pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a51c7-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="a51c7-124">Vytvoření projektu knihovny tříd pro spravované třídy, kterou chcete spustit v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="a51c7-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="a51c7-125">Třída musí mít výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="a51c7-125">The class must have a default constructor.</span></span>  
  
     <span data-ttu-id="a51c7-126">Ověřte, zda máte pro vaše sestavení v souboru AssemblyInfo číslo dokončení sestávající ze čtyř částí verze.</span><span class="sxs-lookup"><span data-stu-id="a51c7-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="a51c7-127">Toto číslo je požadované pro údržbu správy verzí v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a51c7-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="a51c7-128">Další informace o čísla verzí, naleznete v části [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="a51c7-128">For more information about version numbers, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
2.  <span data-ttu-id="a51c7-129">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a51c7-129">On the **Project** menu, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a51c7-130">Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="a51c7-130">Click the **Compile** tab.</span></span>  
  
4.  <span data-ttu-id="a51c7-131">Vyberte **zaregistrovat zprostředkovatel komunikace s objekty COM** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="a51c7-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="a51c7-132">Při sestavování projektu pro zprostředkovatele komunikace s objekty COM se automaticky registruje sestavení.</span><span class="sxs-lookup"><span data-stu-id="a51c7-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="a51c7-133">Pokud vytváříte nativní aplikace [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], sestavení můžete použít klepnutím **přidat odkaz na** na **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="a51c7-133">If you are building a native application in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
#### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="a51c7-134">Chcete-li vytvořit obálka volatelná aplikacemi COM pomocí rozhraní .NET Framework – nástroje</span><span class="sxs-lookup"><span data-stu-id="a51c7-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="a51c7-135">Spustit [Regasm.exe (Nástroj registrace sestavení)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="a51c7-135">Run the [Regasm.exe (Assembly Registration Tool)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
 <span data-ttu-id="a51c7-136">Tento nástroj načte metadata sestavení a přidá nezbytné položky registru.</span><span class="sxs-lookup"><span data-stu-id="a51c7-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="a51c7-137">Klienti COM v důsledku toho můžete vytvořit třídy rozhraní .NET Framework transparentně.</span><span class="sxs-lookup"><span data-stu-id="a51c7-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="a51c7-138">Sestavení můžete použít, jakoby byly nativní třídy COM.</span><span class="sxs-lookup"><span data-stu-id="a51c7-138">You can use the assembly as if it were a native COM class.</span></span>  
  
 <span data-ttu-id="a51c7-139">Můžete spustit Regasm.exe na sestavení se nenachází v libovolného adresáře a poté spusťte [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) ho přesunout do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="a51c7-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="a51c7-140">Přesunutí sestavení zneplatnění umístění položky registru, protože je vždy zkontrolován Pokud sestavení nebyl nalezen jinde v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="a51c7-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a51c7-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="a51c7-141">See Also</span></span>  
 [<span data-ttu-id="a51c7-142">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="a51c7-142">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [<span data-ttu-id="a51c7-143">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="a51c7-143">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)
