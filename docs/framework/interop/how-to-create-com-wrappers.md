---
title: 'Postupy: Vytváření obálek COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 623df8aa86d25d9a57d3039bee01b0ee39d402a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123943"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="e901d-102">Postupy: Vytváření obálek COM</span><span class="sxs-lookup"><span data-stu-id="e901d-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="e901d-103">Obálky modelu COM (Component Object Model) můžete vytvořit pomocí funkcí sady Visual Studio 2005 nebo nástrojů .NET Framework nástroje Tlbimp. exe a Regasm. exe.</span><span class="sxs-lookup"><span data-stu-id="e901d-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="e901d-104">Obě metody generují dva typy wrapperů COM:</span><span class="sxs-lookup"><span data-stu-id="e901d-104">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="e901d-105">[Běhová obálka](../../standard/native-interop/runtime-callable-wrapper.md) , která se má volat z knihovny typů pro spuštění objektu COM ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="e901d-105">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="e901d-106">Obálka s možnostmi [modelu COM](../../standard/native-interop/com-callable-wrapper.md) s požadovaným nastavením registru pro spuštění spravovaného objektu v nativní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e901d-106">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="e901d-107">V aplikaci Visual Studio 2005 můžete přidat obálku COM jako odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="e901d-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="e901d-108">Zabalení objektů COM ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="e901d-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="e901d-109">Vytvoření obálky s požadovanou metodou spuštění pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e901d-109">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="e901d-110">Otevřete projekt pro spravovanou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e901d-110">Open the project for your managed application.</span></span>

2. <span data-ttu-id="e901d-111">V nabídce **projekt** klikněte na příkaz **Zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="e901d-111">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="e901d-112">V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="e901d-112">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="e901d-113">V dialogovém okně Přidat odkaz klikněte na kartu **com** , vyberte komponentu, kterou chcete použít, a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="e901d-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="e901d-114">V **Průzkumník řešení**si všimněte, že komponenta modelu COM je přidána do složky odkazy v projektu.</span><span class="sxs-lookup"><span data-stu-id="e901d-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="e901d-115">Nyní můžete napsat kód pro přístup k objektu COM.</span><span class="sxs-lookup"><span data-stu-id="e901d-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="e901d-116">Můžete začít deklarováním objektu, například pomocí příkazu `Imports` pro Visual Basic nebo příkazu `Using` pro C#.</span><span class="sxs-lookup"><span data-stu-id="e901d-116">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="e901d-117">Pokud chcete programovat součásti systém Microsoft Office komponenty, nejprve nainstalujte [systém Microsoft Office primární spolupráce sestavení](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="e901d-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](https://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="e901d-118">V kroku 4 vyberte nejnovější verzi knihovny objektů, kterou chcete použít pro požadovaný produkt Office, například **knihovnu objektů Microsoft Word 11,0**.</span><span class="sxs-lookup"><span data-stu-id="e901d-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="e901d-119">Vytvoření obálky s požadovanou metodou spuštění pomocí .NET Frameworkch nástrojů</span><span class="sxs-lookup"><span data-stu-id="e901d-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="e901d-120">Spusťte nástroj [Tlbimp. exe (importér knihovny typů)](../tools/tlbimp-exe-type-library-importer.md) .</span><span class="sxs-lookup"><span data-stu-id="e901d-120">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="e901d-121">Tento nástroj vytvoří sestavení, které obsahuje metadata modulu runtime pro typy definované v původní knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="e901d-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="e901d-122">Zabalení spravovaných objektů v nativní aplikaci</span><span class="sxs-lookup"><span data-stu-id="e901d-122">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="e901d-123">Vytvoření obálky s požadovanou metodou COM pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e901d-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="e901d-124">Vytvořte projekt knihovny tříd pro spravovanou třídu, kterou chcete spustit v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="e901d-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="e901d-125">Třída musí mít konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="e901d-125">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="e901d-126">Ověřte, zda máte pro sestavení v souboru AssemblyInfo celé číslo verze se čtyřmi částmi.</span><span class="sxs-lookup"><span data-stu-id="e901d-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="e901d-127">Toto číslo je vyžadováno pro údržbu správy verzí v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e901d-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="e901d-128">Další informace o číslech verzí najdete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="e901d-128">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="e901d-129">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e901d-129">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="e901d-130">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="e901d-130">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="e901d-131">Zaškrtněte políčko **zaregistrovat pro zprostředkovatele komunikace s objekty COM** .</span><span class="sxs-lookup"><span data-stu-id="e901d-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="e901d-132">Při sestavování projektu je sestavení automaticky registrováno pro zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="e901d-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="e901d-133">Pokud vytváříte nativní aplikaci v aplikaci Visual Studio 2005, můžete použít sestavení kliknutím na **Přidat odkaz** v nabídce **projekt** .</span><span class="sxs-lookup"><span data-stu-id="e901d-133">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="e901d-134">Vytvoření obálky s požadovanou metodou COM pomocí .NET Frameworkch nástrojů</span><span class="sxs-lookup"><span data-stu-id="e901d-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="e901d-135">Spusťte nástroj [Regasm. exe (Nástroj pro registraci sestavení)](../tools/regasm-exe-assembly-registration-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="e901d-135">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="e901d-136">Tento nástroj přečte metadata sestavení a přidá nezbytné položky do registru.</span><span class="sxs-lookup"><span data-stu-id="e901d-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="e901d-137">V důsledku toho mohou klienti modelu COM vytvářet .NET Framework třídy transparentně.</span><span class="sxs-lookup"><span data-stu-id="e901d-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="e901d-138">Můžete použít sestavení, jako by šlo o nativní třídu COM.</span><span class="sxs-lookup"><span data-stu-id="e901d-138">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="e901d-139">Můžete spustit nástroj Regasm. exe pro sestavení nacházející se v jakémkoli adresáři a poté spustit nástroj [Gacutil. exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) , aby jej bylo možné přesunout do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="e901d-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="e901d-140">Přesunutí sestavení neověřuje položky registru umístění, protože globální mezipaměť sestavení (GAC) je vždy zkoumána v případě, že sestavení není nalezeno jinde.</span><span class="sxs-lookup"><span data-stu-id="e901d-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e901d-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e901d-141">See also</span></span>

- [<span data-ttu-id="e901d-142">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="e901d-142">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="e901d-143">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="e901d-143">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
