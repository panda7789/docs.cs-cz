---
title: 'Postupy: Odkaz na objekty modelu COM z jazyka Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 694bd74e2b5ae374269accd845fe9178958bf56c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="c3c7f-102">Postupy: Odkaz na objekty modelu COM z jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3c7f-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="c3c7f-103">V [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], přidávání odkazů na objekty modelu COM, které mají knihovny typů vyžaduje vytvoření spolupráce sestavení pro knihovny COM.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="c3c7f-104">Odkazy na členy objektu COM jsou směrovány do sestavení vzájemné spolupráce a předá ji vlastního objektu COM.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="c3c7f-105">Odpovědí z objektu COM jsou směrovány do sestavení vzájemné spolupráce a předávaných do vaší [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application.</span></span>  
  
 <span data-ttu-id="c3c7f-106">Objekt modelu COM bez použití zprostředkovatele komunikace s objekty sestavení vložení informací o typu objektu COM v sestavení rozhraní .NET, můžete odkazovat.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="c3c7f-107">Chcete-li vložit informace o typu, nastavte `Embed Interop Types` vlastnost `True` pro odkaz na objekt COM.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="c3c7f-108">Pokud jste se kompilace pomocí kompilátoru příkazového řádku, použijte `/link` možnost, chcete-li knihovny COM.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="c3c7f-109">Další informace najdete v tématu [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="c3c7f-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="c3c7f-110">Když přidáte odkaz na knihovnu typů z integrované vývojové prostředí (IDE) automaticky vytvoří spolupráce – sestavení.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-110"> automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="c3c7f-111">Při práci z příkazového řádku, můžete použít nástroj Tlbimp ručně vytvořit sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="c3c7f-112">Chcete-li přidat odkazy na objekty modelu COM</span><span class="sxs-lookup"><span data-stu-id="c3c7f-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="c3c7f-113">Na **projektu** nabídce zvolte **přidat odkaz na** a pak klikněte na tlačítko **COM** karta v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="c3c7f-114">Vyberte komponentu, kterou chcete použít v seznamu objektů COM.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="c3c7f-115">Zjednodušení přístupu k sestavení vzájemné spolupráce, přidejte `Imports` příkaz do horní části třídy nebo modul, ve které budete používat objekt COM.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="c3c7f-116">Například následující příklad kódu importuje obor názvů `INKEDLib` pro objekty v odkazuje `Microsoft InkEdit Control 1.0` knihovny.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="c3c7f-117">Chcete-li vytvořit pomocí Tlbimp sestavení spolupráce</span><span class="sxs-lookup"><span data-stu-id="c3c7f-117">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="c3c7f-118">Přidejte umístění Tlbimp do cesty k vyhledávání, pokud již není součástí cesta hledání a nejste aktuálně v adresáři, kde se nachází.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="c3c7f-119">Volání Tlbimp z příkazového řádku, poskytuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="c3c7f-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="c3c7f-120">Název a umístění knihovny DLL, která obsahuje knihovny typů</span><span class="sxs-lookup"><span data-stu-id="c3c7f-120">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="c3c7f-121">Název a umístění oboru názvů, kde má být umístěn informace</span><span class="sxs-lookup"><span data-stu-id="c3c7f-121">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="c3c7f-122">Název a umístění cíl sestavení spolupráce</span><span class="sxs-lookup"><span data-stu-id="c3c7f-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="c3c7f-123">Následující kód představuje příklad:</span><span class="sxs-lookup"><span data-stu-id="c3c7f-123">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="c3c7f-124">Tlbimp slouží k vytvoření spolupráce – sestavení pro knihovny typů, i pro zrušení registrace COM – objekty.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="c3c7f-125">Objekty COM, na kterou odkazuje sestavení vzájemné spolupráce však musí být správně zaregistrován, na počítači, kde mají být použity.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="c3c7f-126">Objekt modelu COM můžete zaregistrovat pomocí nástroje Regsvr32 součástí operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c3c7f-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3c7f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3c7f-127">See Also</span></span>  
 [<span data-ttu-id="c3c7f-128">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="c3c7f-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="c3c7f-129">Tlbimp.exe (Importér knihovny)</span><span class="sxs-lookup"><span data-stu-id="c3c7f-129">Tlbimp.exe (Type Library Importer)</span></span>](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [<span data-ttu-id="c3c7f-130">Tlbexp.exe (Exportér knihovny)</span><span class="sxs-lookup"><span data-stu-id="c3c7f-130">Tlbexp.exe (Type Library Exporter)</span></span>](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [<span data-ttu-id="c3c7f-131">Návod: Implementace dědičnosti s objekty COM</span><span class="sxs-lookup"><span data-stu-id="c3c7f-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="c3c7f-132">Řešení potíží s interoperabilitou</span><span class="sxs-lookup"><span data-stu-id="c3c7f-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [<span data-ttu-id="c3c7f-133">Imports – příkaz (Namespace .NET a typ)</span><span class="sxs-lookup"><span data-stu-id="c3c7f-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
