---
title: 'Postupy: Vytváření obálek COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 035d6439ec90426d7b68e05043ea8b6722f81d28
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121603"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="19fcf-102">Postupy: Vytváření obálek COM</span><span class="sxs-lookup"><span data-stu-id="19fcf-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="19fcf-103">Obálky modelu COM (Component Object Model) můžete vytvořit pomocí funkcí sady Visual Studio 2005 nebo nástrojů .NET Framework nástroje Tlbimp. exe a Regasm. exe.</span><span class="sxs-lookup"><span data-stu-id="19fcf-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="19fcf-104">Obě metody generují dva typy wrapperů COM:</span><span class="sxs-lookup"><span data-stu-id="19fcf-104">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="19fcf-105">[Běhová obálka](../../standard/native-interop/runtime-callable-wrapper.md) , která se má volat z knihovny typů pro spuštění objektu COM ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="19fcf-105">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="19fcf-106">Obálka s možnostmi [modelu COM](../../standard/native-interop/com-callable-wrapper.md) s požadovaným nastavením registru pro spuštění spravovaného objektu v nativní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="19fcf-106">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="19fcf-107">V aplikaci Visual Studio 2005 můžete přidat obálku COM jako odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="19fcf-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="19fcf-108">Zabalení objektů COM ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="19fcf-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="19fcf-109">Vytvoření obálky s požadovanou metodou spuštění pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="19fcf-109">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="19fcf-110">Otevřete projekt pro spravovanou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="19fcf-110">Open the project for your managed application.</span></span>

2. <span data-ttu-id="19fcf-111">V nabídce **projekt** klikněte na příkaz **Zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="19fcf-111">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="19fcf-112">V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="19fcf-112">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="19fcf-113">V dialogovém okně Přidat odkaz klikněte na kartu **com** , vyberte komponentu, kterou chcete použít, a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="19fcf-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="19fcf-114">V **Průzkumník řešení**si všimněte, že komponenta modelu COM je přidána do složky odkazy v projektu.</span><span class="sxs-lookup"><span data-stu-id="19fcf-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="19fcf-115">Nyní můžete napsat kód pro přístup k objektu COM.</span><span class="sxs-lookup"><span data-stu-id="19fcf-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="19fcf-116">Můžete začít deklarováním objektu, například pomocí `Imports` příkazu pro Visual Basic nebo `Using` příkazu pro jazyk C#.</span><span class="sxs-lookup"><span data-stu-id="19fcf-116">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="19fcf-117">Pokud chcete programovat systém Microsoft Office komponenty, nejprve nainstalujte [systém Microsoft Office primární spolupracující sestavení](https://www.microsoft.com/Download/details.aspx?id=3508).</span><span class="sxs-lookup"><span data-stu-id="19fcf-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies Redistributable](https://www.microsoft.com/Download/details.aspx?id=3508).</span></span>
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="19fcf-118">Vytvoření obálky s požadovanou metodou spuštění pomocí .NET Frameworkch nástrojů</span><span class="sxs-lookup"><span data-stu-id="19fcf-118">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="19fcf-119">Spusťte nástroj [Tlbimp. exe (importér knihovny typů)](../tools/tlbimp-exe-type-library-importer.md) .</span><span class="sxs-lookup"><span data-stu-id="19fcf-119">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="19fcf-120">Tento nástroj vytvoří sestavení, které obsahuje metadata modulu runtime pro typy definované v původní knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="19fcf-120">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="19fcf-121">Zabalení spravovaných objektů v nativní aplikaci</span><span class="sxs-lookup"><span data-stu-id="19fcf-121">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="19fcf-122">Vytvoření obálky s požadovanou metodou COM pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="19fcf-122">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="19fcf-123">Vytvořte projekt knihovny tříd pro spravovanou třídu, kterou chcete spustit v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="19fcf-123">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="19fcf-124">Třída musí mít konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="19fcf-124">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="19fcf-125">Ověřte, zda máte pro sestavení v souboru AssemblyInfo celé číslo verze se čtyřmi částmi.</span><span class="sxs-lookup"><span data-stu-id="19fcf-125">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="19fcf-126">Toto číslo je vyžadováno pro údržbu správy verzí v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="19fcf-126">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="19fcf-127">Další informace o číslech verzí najdete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="19fcf-127">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="19fcf-128">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="19fcf-128">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="19fcf-129">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="19fcf-129">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="19fcf-130">Zaškrtněte políčko **zaregistrovat pro zprostředkovatele komunikace s objekty COM** .</span><span class="sxs-lookup"><span data-stu-id="19fcf-130">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="19fcf-131">Při sestavování projektu je sestavení automaticky registrováno pro zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="19fcf-131">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="19fcf-132">Pokud vytváříte nativní aplikaci v aplikaci Visual Studio 2005, můžete použít sestavení kliknutím na **Přidat odkaz** v nabídce **projekt** .</span><span class="sxs-lookup"><span data-stu-id="19fcf-132">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="19fcf-133">Vytvoření obálky s požadovanou metodou COM pomocí .NET Frameworkch nástrojů</span><span class="sxs-lookup"><span data-stu-id="19fcf-133">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="19fcf-134">Spusťte nástroj [Regasm. exe (Nástroj pro registraci sestavení)](../tools/regasm-exe-assembly-registration-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="19fcf-134">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="19fcf-135">Tento nástroj přečte metadata sestavení a přidá nezbytné položky do registru.</span><span class="sxs-lookup"><span data-stu-id="19fcf-135">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="19fcf-136">V důsledku toho mohou klienti modelu COM vytvářet .NET Framework třídy transparentně.</span><span class="sxs-lookup"><span data-stu-id="19fcf-136">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="19fcf-137">Můžete použít sestavení, jako by šlo o nativní třídu COM.</span><span class="sxs-lookup"><span data-stu-id="19fcf-137">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="19fcf-138">Můžete spustit nástroj Regasm. exe pro sestavení nacházející se v jakémkoli adresáři a poté spustit nástroj [Gacutil. exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) , aby jej bylo možné přesunout do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="19fcf-138">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="19fcf-139">Přesunutí sestavení neověřuje položky registru umístění, protože globální mezipaměť sestavení (GAC) je vždy zkoumána v případě, že sestavení není nalezeno jinde.</span><span class="sxs-lookup"><span data-stu-id="19fcf-139">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19fcf-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="19fcf-140">See also</span></span>

- [<span data-ttu-id="19fcf-141">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="19fcf-141">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="19fcf-142">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="19fcf-142">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
