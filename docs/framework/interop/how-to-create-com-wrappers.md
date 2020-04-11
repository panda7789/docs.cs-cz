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
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="8d3b0-102">Postupy: Vytváření obálek COM</span><span class="sxs-lookup"><span data-stu-id="8d3b0-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="8d3b0-103">Obálky com (Com) můžete vytvořit pomocí funkcí sady Visual Studio 2005 nebo nástrojů rozhraní Tlbimp.exe a Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="8d3b0-104">Obě metody generují dva typy obalů com:</span><span class="sxs-lookup"><span data-stu-id="8d3b0-104">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="8d3b0-105">[Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) z knihovny typů pro spuštění objektu COM ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-105">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="8d3b0-106">Com [Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) s požadovaným nastavením registru pro spuštění spravovaného objektu v nativní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-106">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="8d3b0-107">V sadě Visual Studio 2005 můžete přidat obálku COM jako odkaz na váš projekt.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="8d3b0-108">Zalamování objektů COM ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="8d3b0-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="8d3b0-109">Vytvoření runtime volatelnéobálky pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8d3b0-109">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="8d3b0-110">Otevřete projekt pro spravovanou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-110">Open the project for your managed application.</span></span>

2. <span data-ttu-id="8d3b0-111">V nabídce **Project** klepněte na příkaz **Zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-111">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="8d3b0-112">V nabídce **Project** klepněte na **tlačítko Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-112">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="8d3b0-113">V dialogovém okně Přidat odkaz klepněte na kartu **COM,** vyberte komponentu, kterou chcete použít, a klepněte na **tlačítko OK**.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="8d3b0-114">V **Průzkumníku řešení**si všimněte, že komponenta MODELU COM je přidána do složky Reference v projektu.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="8d3b0-115">Nyní můžete napsat kód pro přístup k objektu COM.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="8d3b0-116">Můžete začít deklarováním objektu, `Imports` například s příkazem pro visual basic nebo příkazem `Using` pro C#.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-116">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="8d3b0-117">Chcete-li naprogramovat součásti sady Microsoft Office, nainstalujte nejprve [redistribuovatelné sestavení primárních meziop sady Microsoft Office](https://www.microsoft.com/Download/details.aspx?id=3508).</span><span class="sxs-lookup"><span data-stu-id="8d3b0-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies Redistributable](https://www.microsoft.com/Download/details.aspx?id=3508).</span></span>
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="8d3b0-118">Vytvoření runtime volatelnéobálky pomocí nástrojů rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8d3b0-118">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="8d3b0-119">Spusťte nástroj [Tlbimp.exe (Import type library).](../tools/tlbimp-exe-type-library-importer.md)</span><span class="sxs-lookup"><span data-stu-id="8d3b0-119">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="8d3b0-120">Tento nástroj vytvoří sestavení, které obsahuje metadata za běhu pro typy definované v původní knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-120">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="8d3b0-121">Zalamování spravovaných objektů v nativní aplikaci</span><span class="sxs-lookup"><span data-stu-id="8d3b0-121">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="8d3b0-122">Vytvoření popisku s volatelným pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8d3b0-122">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="8d3b0-123">Vytvořte projekt knihovny tříd pro spravovanou třídu, kterou chcete spustit v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-123">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="8d3b0-124">Třída musí mít konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-124">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="8d3b0-125">Ověřte, zda máte úplné číslo čtyřdílné verze pro sestavení v souboru AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-125">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="8d3b0-126">Toto číslo je vyžadováno pro údržbu správy verzí v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-126">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="8d3b0-127">Další informace o číslech verzí naleznete v [tématu Správa verzí sestavení](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="8d3b0-127">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="8d3b0-128">V nabídce **Project** klepněte na **položku Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-128">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="8d3b0-129">Klikněte na kartu **Kompilace.**</span><span class="sxs-lookup"><span data-stu-id="8d3b0-129">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="8d3b0-130">Zaškrtněte políčko **Registrovat se pro interop com.**</span><span class="sxs-lookup"><span data-stu-id="8d3b0-130">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="8d3b0-131">Při vytváření projektu je sestavení automaticky registrováno pro interop COM.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-131">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="8d3b0-132">Pokud vytváříte nativní aplikaci v sadě Visual Studio 2005, můžete toto sestavení použít klepnutím na tlačítko **Přidat odkaz** v nabídce **Projekt.**</span><span class="sxs-lookup"><span data-stu-id="8d3b0-132">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="8d3b0-133">Vytvoření volatelnéobálky COM pomocí nástrojů rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8d3b0-133">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="8d3b0-134">Spusťte nástroj [Regasm.exe (Nástroj pro registraci sestavy).](../tools/regasm-exe-assembly-registration-tool.md)</span><span class="sxs-lookup"><span data-stu-id="8d3b0-134">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="8d3b0-135">Tento nástroj přečte metadata sestavení a přidá potřebné položky do registru.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-135">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="8d3b0-136">V důsledku toho mohou klienti COM vytvářet třídy rozhraní .NET Framework transparentně.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-136">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="8d3b0-137">Sestavení můžete použít, jako by se jednalo o nativní třídu COM.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-137">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="8d3b0-138">Regasm.exe můžete spustit v sestavení umístěném v libovolném adresáři a potom spustit [soubor Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) a přesunout jej do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-138">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="8d3b0-139">Přesunutím sestavení není zneplatnění položky registru umístění, protože globální mezipaměť sestavení je vždy zkontrolována, pokud není sestavení nalezeno jinde.</span><span class="sxs-lookup"><span data-stu-id="8d3b0-139">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d3b0-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d3b0-140">See also</span></span>

- [<span data-ttu-id="8d3b0-141">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="8d3b0-141">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="8d3b0-142">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="8d3b0-142">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
