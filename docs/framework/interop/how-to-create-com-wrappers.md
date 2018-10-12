---
title: 'Postupy: Vytváření obálek COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14bf011c3711a267b8cf5a1fc0497a347468387d
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121750"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="b6a26-102">Postupy: Vytváření obálek COM</span><span class="sxs-lookup"><span data-stu-id="b6a26-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="b6a26-103">Obálky objektu modelu COM (Component) můžete vytvořit pomocí funkce sady Visual Studio 2005 nebo rozhraní .NET Framework nástroje Tlbimp.exe a Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="b6a26-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="b6a26-104">Obě metody vygenerovat dva typy COM – obálky:</span><span class="sxs-lookup"><span data-stu-id="b6a26-104">Both methods generate two types of COM wrappers:</span></span>

-   <span data-ttu-id="b6a26-105">A [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) z knihovny typů pro spuštění objekt modelu COM ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="b6a26-105">A [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

-   <span data-ttu-id="b6a26-106">A [obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md) s se požadovaná nastavení registru pro spuštění spravovaného objektu v nativní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b6a26-106">A [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="b6a26-107">V sadě Visual Studio 2005 můžete přidat obálky COM jako odkaz na svůj projekt.</span><span class="sxs-lookup"><span data-stu-id="b6a26-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="b6a26-108">Objekty COM zabalte ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="b6a26-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="b6a26-109">Chcete-li vytvořit obálka volatelná za běhu pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b6a26-109">To create a runtime callable wrapper using Visual Studio</span></span>

1.  <span data-ttu-id="b6a26-110">Otevřete projekt pro spravovanou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b6a26-110">Open the project for your managed application.</span></span>

2.  <span data-ttu-id="b6a26-111">Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="b6a26-111">On the **Project** menu, click **Show All Files**.</span></span>

3.  <span data-ttu-id="b6a26-112">Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="b6a26-112">On the **Project** menu, click **Add Reference**.</span></span>

4.  <span data-ttu-id="b6a26-113">V dialogovém okně Přidat odkaz na tlačítko **COM** kartu, vyberte komponentu, kterou chcete použít a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6a26-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="b6a26-114">V **Průzkumníka řešení**, mějte na paměti, že komponenty modelu COM je přidán do složky odkazy ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="b6a26-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="b6a26-115">Teď můžete psát kód pro přístup k objektu COM.</span><span class="sxs-lookup"><span data-stu-id="b6a26-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="b6a26-116">Můžete začít deklarováním objektu, například pomocí `Imports` příkaz pro [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nebo `Using` příkaz pro [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b6a26-116">You can begin by declaring the object, such as with an `Imports` statement for [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] or a `Using` statement for [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="b6a26-117">Pokud chcete program komponenty Microsoft Office, nejdřív nainstalovat [Microsoft Office Primary Interop Assemblies](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="b6a26-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](https://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="b6a26-118">V kroku 4, vyberte nejnovější verzi k dispozici produktu Office, jako například chcete objekt knihovny **Microsoft Word 11.0 objekt knihovny**.</span><span class="sxs-lookup"><span data-stu-id="b6a26-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="b6a26-119">Chcete-li vytvořit obálka volatelná za běhu pomocí rozhraní .NET Framework – nástroje</span><span class="sxs-lookup"><span data-stu-id="b6a26-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="b6a26-120">Spustit [Tlbimp.exe (Importér knihovny typů)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="b6a26-120">Run the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="b6a26-121">Tento nástroj vytvoří sestavení, který obsahuje metadat v době běhu pro typy definované v původní knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="b6a26-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="b6a26-122">Uveďte spravované objekty v nativní aplikaci</span><span class="sxs-lookup"><span data-stu-id="b6a26-122">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="b6a26-123">Chcete-li vytvořit obálka volatelná aplikacemi COM pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b6a26-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="b6a26-124">Vytvořte projekt knihovny tříd pro spravované třídy, které chcete spouštět v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="b6a26-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="b6a26-125">Třída musí mít výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b6a26-125">The class must have a default constructor.</span></span>  
  
     <span data-ttu-id="b6a26-126">Ověřte, že máte číslo úplné verze složené ze čtyř částí pro vaše sestavení v souboru AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="b6a26-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="b6a26-127">Toto číslo je vyžadován pro zachování verzí v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="b6a26-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="b6a26-128">Další informace o číslech verzí najdete v tématu [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="b6a26-128">For more information about version numbers, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
2.  <span data-ttu-id="b6a26-129">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b6a26-129">On the **Project** menu, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="b6a26-130">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="b6a26-130">Click the **Compile** tab.</span></span>  
  
4.  <span data-ttu-id="b6a26-131">Vyberte **zaregistrovat pro interoperabilitu COM** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="b6a26-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="b6a26-132">Při vytváření projektu pro zprostředkovatele komunikace s objekty COM se automaticky registruje sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6a26-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="b6a26-133">Pokud vytváříte nativní aplikace v sadě Visual Studio 2005, můžete kliknutím na použít sestavení **přidat odkaz** na **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="b6a26-133">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="b6a26-134">Chcete-li vytvořit obálka volatelná aplikacemi COM pomocí rozhraní .NET Framework – nástroje</span><span class="sxs-lookup"><span data-stu-id="b6a26-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="b6a26-135">Spustit [Regasm.exe (Nástroj registrace sestavení)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="b6a26-135">Run the [Regasm.exe (Assembly Registration Tool)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="b6a26-136">Tento nástroj načte metadata sestavení a přidá nezbytné položky registru.</span><span class="sxs-lookup"><span data-stu-id="b6a26-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="b6a26-137">Klienti modelu COM v důsledku toho můžete vytvořit třídy rozhraní .NET Framework transparentně.</span><span class="sxs-lookup"><span data-stu-id="b6a26-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="b6a26-138">Sestavení můžete použít, jako by šlo nativních tříd modelu COM.</span><span class="sxs-lookup"><span data-stu-id="b6a26-138">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="b6a26-139">Můžete spustit Regasm.exe na sestavení se nenachází v žádné adresáře a spusťte [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) ji přesunout do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6a26-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="b6a26-140">Přesun sestavení nedojde k zneplatnění umístění položky registru, protože globální mezipaměti sestavení je vždy zkontrolován, pokud se sestavení nenajde jinde.</span><span class="sxs-lookup"><span data-stu-id="b6a26-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6a26-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6a26-141">See also</span></span>  

- [<span data-ttu-id="b6a26-142">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="b6a26-142">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)  
- [<span data-ttu-id="b6a26-143">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="b6a26-143">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)