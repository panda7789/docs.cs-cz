---
title: 'Postupy: Odkaz na objekty modelu COM z jazyka Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: ea0e1d9b0ae9f151d901c425512508ba7bc05343
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524359"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="3cbde-102">Postupy: Odkaz na objekty modelu COM z jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3cbde-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="3cbde-103">V Visual Basic přidávání odkazů na objekty modelu COM, které mají knihovny typů, vyžaduje vytvoření sestavení vzájemné spolupráce pro knihovnu COM.</span><span class="sxs-lookup"><span data-stu-id="3cbde-103">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="3cbde-104">Odkazy na členy objektu COM jsou směrovány do sestavení vzájemné spolupráce a poté předány do skutečného objektu COM.</span><span class="sxs-lookup"><span data-stu-id="3cbde-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="3cbde-105">Odpovědi z objektu COM jsou směrovány do sestavení vzájemné spolupráce a předány do vaší aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3cbde-105">Responses from the COM object are routed to the interop assembly and forwarded to your .NET Framework application.</span></span>  
  
 <span data-ttu-id="3cbde-106">Můžete odkazovat na objekt modelu COM bez použití definičního sestavení vložením informací o typu pro objekt modelu COM v sestavení .NET.</span><span class="sxs-lookup"><span data-stu-id="3cbde-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="3cbde-107">Pro vložení informací o typu nastavte vlastnost `Embed Interop Types` na `True` pro odkaz na objekt COM.</span><span class="sxs-lookup"><span data-stu-id="3cbde-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="3cbde-108">Pokud kompilujete pomocí kompilátoru příkazového řádku, použijte možnost `/link` pro odkaz na knihovnu COM.</span><span class="sxs-lookup"><span data-stu-id="3cbde-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="3cbde-109">Další informace najdete v tématu [-Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="3cbde-109">For more information, see [-link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="3cbde-110">Visual Basic automaticky vytvoří sestavení vzájemné spolupráce, když přidáte odkaz na knihovnu typů z integrovaného vývojového prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="3cbde-110">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="3cbde-111">Při práci z příkazového řádku můžete použít nástroj Tlbimp k ručnímu vytváření sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="3cbde-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="3cbde-112">Přidání odkazů do objektů COM</span><span class="sxs-lookup"><span data-stu-id="3cbde-112">To add references to COM objects</span></span>  
  
1. <span data-ttu-id="3cbde-113">V nabídce **projekt** zvolte možnost **Přidat odkaz** a potom v dialogovém okně klikněte na kartu **com** .</span><span class="sxs-lookup"><span data-stu-id="3cbde-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2. <span data-ttu-id="3cbde-114">Vyberte součást, kterou chcete použít, ze seznamu objektů COM.</span><span class="sxs-lookup"><span data-stu-id="3cbde-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3. <span data-ttu-id="3cbde-115">Chcete-li zjednodušit přístup k definičnímu sestavení, přidejte příkaz `Imports` na začátek třídy nebo modulu, ve kterém budete používat objekt COM.</span><span class="sxs-lookup"><span data-stu-id="3cbde-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="3cbde-116">Například následující příklad kódu importuje obor názvů `INKEDLib` pro objekty, na které je odkazováno v knihovně `Microsoft InkEdit Control 1.0`.</span><span class="sxs-lookup"><span data-stu-id="3cbde-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="3cbde-117">Vytvoření sestavení vzájemné spolupráce pomocí Tlbimp</span><span class="sxs-lookup"><span data-stu-id="3cbde-117">To create an interop assembly using Tlbimp</span></span>  
  
1. <span data-ttu-id="3cbde-118">Přidejte umístění Tlbimp do cesty pro hledání, pokud již není součástí cesty pro hledání a že aktuálně nejste v adresáři, kde je umístěn.</span><span class="sxs-lookup"><span data-stu-id="3cbde-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2. <span data-ttu-id="3cbde-119">Volání Tlbimp z příkazového řádku, který poskytuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="3cbde-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    - <span data-ttu-id="3cbde-120">Název a umístění knihovny DLL, která obsahuje knihovnu typů</span><span class="sxs-lookup"><span data-stu-id="3cbde-120">Name and location of the DLL that contains the type library</span></span>  
  
    - <span data-ttu-id="3cbde-121">Název a umístění oboru názvů, kde se mají informace umístit</span><span class="sxs-lookup"><span data-stu-id="3cbde-121">Name and location of the namespace where the information should be placed</span></span>  
  
    - <span data-ttu-id="3cbde-122">Název a umístění cílového definičního sestavení</span><span class="sxs-lookup"><span data-stu-id="3cbde-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="3cbde-123">Následující kód poskytuje příklad:</span><span class="sxs-lookup"><span data-stu-id="3cbde-123">The following code provides an example:</span></span>  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="3cbde-124">Pomocí nástroje Tlbimp můžete vytvořit definiční sestavení pro knihovny typů, a to i pro neregistrované objekty COM.</span><span class="sxs-lookup"><span data-stu-id="3cbde-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="3cbde-125">Nicméně objekty COM, na které odkazují sestavení interop, musí být správně registrovány v počítači, kde mají být použity.</span><span class="sxs-lookup"><span data-stu-id="3cbde-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="3cbde-126">Objekt COM můžete zaregistrovat pomocí nástroje Regsvr32, který je součástí operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3cbde-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cbde-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cbde-127">See also</span></span>

- [<span data-ttu-id="3cbde-128">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="3cbde-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="3cbde-129">Tlbimp.exe (importér knihovny typů)</span><span class="sxs-lookup"><span data-stu-id="3cbde-129">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="3cbde-130">Tlbexp.exe (exportér knihovny typů)</span><span class="sxs-lookup"><span data-stu-id="3cbde-130">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="3cbde-131">Návod: Implementace dědičnosti pomocí objektů COM</span><span class="sxs-lookup"><span data-stu-id="3cbde-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="3cbde-132">Řešení potíží s interoperabilitou</span><span class="sxs-lookup"><span data-stu-id="3cbde-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [<span data-ttu-id="3cbde-133">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="3cbde-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
