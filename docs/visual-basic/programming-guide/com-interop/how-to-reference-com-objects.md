---
title: 'Postupy: Objekty odkaz modelu COM z jazyka Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 0327c497025630747e526503556f4a1705948850
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295260"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="cf8a1-102">Postupy: Objekty odkaz modelu COM z jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf8a1-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="cf8a1-103">V jazyce Visual Basic přidávání odkazů na objekty modelu COM, které mají knihovny typů vyžaduje vytvoření sestavení vzájemné spolupráce pro knihovnu COM.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-103">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="cf8a1-104">Odkazy na členy objektu modelu COM jsou směrovány na sestavení vzájemné spolupráce a pak se předávají do vlastního objektu COM.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="cf8a1-105">Odpovědi z objektu modelu COM jsou směrovány na sestavení vzájemné spolupráce a předá vaší [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application.</span></span>  
  
 <span data-ttu-id="cf8a1-106">Můžete odkazovat na objekt modelu COM bez použití sestavení vzájemné spolupráce s využitím vkládání služby informace o objektu modelu COM typu v sestavení .NET.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="cf8a1-107">Chcete-li vložit informace o typu, nastavte `Embed Interop Types` vlastnost `True` pro odkaz na objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="cf8a1-108">Pokud kompilujete pomocí kompilátoru příkazového řádku, použijte `/link` možnost odkazovat na knihovny COM.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="cf8a1-109">Další informace najdete v tématu [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="cf8a1-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="cf8a1-110">Visual Basic automaticky vytvoří sestavení vzájemné spolupráce, když přidáte odkaz na knihovnu typů z integrovaného vývojového prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="cf8a1-110">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="cf8a1-111">Při práci z příkazového řádku, můžete použít nástroj Tlbimp můžete ručně vytvořit sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="cf8a1-112">Chcete-li přidat odkazy na objekty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-112">To add references to COM objects</span></span>  
  
1. <span data-ttu-id="cf8a1-113">Na **projektu** nabídce zvolte **přidat odkaz** a potom klikněte na tlačítko **COM** kartu v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2. <span data-ttu-id="cf8a1-114">Vyberte komponentu, kterou chcete použít v seznamu objektů COM.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3. <span data-ttu-id="cf8a1-115">Chcete-li zjednodušit přístup ke zprostředkovatelům sestavení, přidejte `Imports` příkaz do horní části třídy nebo modulu, ve které budete používat objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="cf8a1-116">Například následující příklad importuje obor názvů `INKEDLib` pro objekty, odkazuje `Microsoft InkEdit Control 1.0` knihovny.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="cf8a1-117">Chcete-li vytvořit sestavení vzájemné spolupráce pomocí Tlbimp</span><span class="sxs-lookup"><span data-stu-id="cf8a1-117">To create an interop assembly using Tlbimp</span></span>  
  
1. <span data-ttu-id="cf8a1-118">Přidejte umístění testovaného Tlbimp do cesty pro hledání, pokud již není součástí cesty pro hledání a nejste momentálně v adresáři, kde se nachází.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2. <span data-ttu-id="cf8a1-119">Volání Tlbimp z příkazového řádku, zadejte následující informace:</span><span class="sxs-lookup"><span data-stu-id="cf8a1-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="cf8a1-120">Název a umístění knihovny DLL, která obsahuje knihovny typů</span><span class="sxs-lookup"><span data-stu-id="cf8a1-120">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="cf8a1-121">Název a umístění oboru názvů, kde by měl být umístěn informace</span><span class="sxs-lookup"><span data-stu-id="cf8a1-121">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="cf8a1-122">Název a umístění cílové sestavení vzájemné spolupráce</span><span class="sxs-lookup"><span data-stu-id="cf8a1-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="cf8a1-123">Následující kód představuje příklad:</span><span class="sxs-lookup"><span data-stu-id="cf8a1-123">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="cf8a1-124">Tlbimp slouží k vytvoření sestavení vzájemné spolupráce pro knihovny typů, i pro registrace modelu COM objekty.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="cf8a1-125">Objekty COM, na které odkazuje sestavení vzájemné spolupráce ale musí být správně zaregistrovaný, na počítači, kde jsou, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="cf8a1-126">Objekt modelu COM lze zaregistrovat pomocí nástroje Regsvr32 zahrnuty s operačním systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="cf8a1-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf8a1-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf8a1-127">See also</span></span>

- [<span data-ttu-id="cf8a1-128">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="cf8a1-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="cf8a1-129">Tlbimp.exe (importér knihovny typů)</span><span class="sxs-lookup"><span data-stu-id="cf8a1-129">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="cf8a1-130">Tlbexp.exe (exportér knihovny typů)</span><span class="sxs-lookup"><span data-stu-id="cf8a1-130">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="cf8a1-131">Návod: Implementace dědičnosti s objekty COM</span><span class="sxs-lookup"><span data-stu-id="cf8a1-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="cf8a1-132">Řešení potíží s interoperabilitou</span><span class="sxs-lookup"><span data-stu-id="cf8a1-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [<span data-ttu-id="cf8a1-133">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="cf8a1-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
