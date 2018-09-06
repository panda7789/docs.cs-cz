---
title: -link (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: 91eba53eb8094e55af09d406515dad16fc71937d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891824"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="0627e-102">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0627e-102">-link (Visual Basic)</span></span>
<span data-ttu-id="0627e-103">Způsobí, že kompilátor pro zpřístupnění informací o typu modelu COM v zadaném sestavení pro projekt, který je aktuálně kompilován.</span><span class="sxs-lookup"><span data-stu-id="0627e-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0627e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0627e-104">Syntax</span></span>  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="0627e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0627e-105">Arguments</span></span>  
  
|<span data-ttu-id="0627e-106">Termín</span><span class="sxs-lookup"><span data-stu-id="0627e-106">Term</span></span>|<span data-ttu-id="0627e-107">Definice</span><span class="sxs-lookup"><span data-stu-id="0627e-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="0627e-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0627e-108">Required.</span></span> <span data-ttu-id="0627e-109">Čárkami oddělený seznam názvů souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="0627e-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="0627e-110">Pokud název souboru obsahuje mezery, uzavřete název do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="0627e-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0627e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0627e-111">Remarks</span></span>  
 <span data-ttu-id="0627e-112">`-link` Možnost můžete nasazovat aplikace, která obsahuje vložené informace o typu.</span><span class="sxs-lookup"><span data-stu-id="0627e-112">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="0627e-113">Aplikace pak můžete použít typy v sestavení modulu runtime, které implementují informace o vloženém typu bez nutnosti odkaz na sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0627e-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="0627e-114">Pokud různé verze sestavení modulu runtime jsou publikovány, aplikace, která obsahuje informace o vloženém typu můžete pracovat se různé verze, aniž byste museli být překompilovány.</span><span class="sxs-lookup"><span data-stu-id="0627e-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="0627e-115">Příklad najdete v tématu [návod: vložení typů ze spravovaných sestavení](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="0627e-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="0627e-116">Použití `-link` volba je užitečná při práci se spoluprací COM.</span><span class="sxs-lookup"><span data-stu-id="0627e-116">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="0627e-117">Můžete vložit typy modelu COM, tak, aby vaše aplikace vyžaduje již primární definiční sestavení (PIA) na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="0627e-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="0627e-118">`-link` Možnost dává pokyn kompilátoru k vložení informací o typu modelu COM z odkazované sestavení vzájemné spolupráce do výsledné zkompilovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="0627e-118">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="0627e-119">Typ modelu COM je identifikován hodnota CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="0627e-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="0627e-120">V důsledku toho může vaše aplikace spouštět na cílovém počítači, který má nainstalovanou stejné typy modelu COM se stejnými hodnotami identifikátoru CLSID.</span><span class="sxs-lookup"><span data-stu-id="0627e-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="0627e-121">Dobrým příkladem jsou aplikace, které automatizují Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="0627e-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="0627e-122">Protože aplikace, jako je Office obvykle ponechat stejnou hodnotu CLSID napříč různými verzemi, aplikace může používat odkazované typy modelu COM v cílovém počítači je nainstalované rozhraní .NET Framework 4 nebo vyšší a vaše aplikace používá metody, vlastnosti, nebo události, které jsou zahrnuty v odkazovaných typů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0627e-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="0627e-123">`-link` Možnost vloží pouze rozhraní, struktury a delegátů.</span><span class="sxs-lookup"><span data-stu-id="0627e-123">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="0627e-124">Vložení třídy modelu COM není podporováno.</span><span class="sxs-lookup"><span data-stu-id="0627e-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0627e-125">Při vytváření instance vloženého typu modelu COM ve vašem kódu, musíte vytvořit instanci pomocí odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0627e-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="0627e-126">Pokus o vytvoření instance vloženého typu modelu COM s použitím CoClass způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="0627e-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="0627e-127">Chcete-li nastavit `-link` v aplikaci Visual Studio, přidejte odkaz na sestavení a nastavte `Embed Interop Types` vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="0627e-127">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="0627e-128">Výchozí nastavení pro `Embed Interop Types` vlastnost **false**.</span><span class="sxs-lookup"><span data-stu-id="0627e-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="0627e-129">Pokud jste se k sestavení modelu COM (sestavení A) která sama odkazuje na jiné sestavení modelu COM (sestavení B), budete mít taky odkaz na sestavení B, pokud je splněna jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="0627e-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="0627e-130">Typ v sestavení A je odvozen z typu nebo implementuje rozhraní ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="0627e-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="0627e-131">Pole, vlastnosti, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="0627e-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="0627e-132">Použití [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) určit adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="0627e-132">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="0627e-133">Jako [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) – možnost kompilátoru, `-link` – možnost kompilátoru používá soubor Vbc.rsp odpovědi, které odkazy se často používá [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="0627e-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="0627e-134">Použít [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) Pokud nechcete, aby kompilátor používal soubor Vbc.rsp – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0627e-134">Use the [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="0627e-135">Krátký tvar `-link` je `-l`.</span><span class="sxs-lookup"><span data-stu-id="0627e-135">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="0627e-136">Obecných typů a vestavěné typy</span><span class="sxs-lookup"><span data-stu-id="0627e-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="0627e-137">Omezení týkající se použití obecných typů v aplikacích, které vložit typy spolupráce v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="0627e-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="0627e-138">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="0627e-138">Generic Interfaces</span></span>  
 <span data-ttu-id="0627e-139">Obecná rozhraní, které jsou vloženy z definičního sestavení nelze použít.</span><span class="sxs-lookup"><span data-stu-id="0627e-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="0627e-140">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0627e-140">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="0627e-141">Typy, které mají obecné parametry.</span><span class="sxs-lookup"><span data-stu-id="0627e-141">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="0627e-142">Typy, které mají obecný parametr, jehož typ je vložen z definičního sestavení nelze použít, pokud je tento typ z externího sestavení.</span><span class="sxs-lookup"><span data-stu-id="0627e-142">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="0627e-143">Toto omezení se nevztahuje na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0627e-143">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="0627e-144">Představme si třeba, <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, která je definována v <xref:Microsoft.Office.Interop.Excel> sestavení.</span><span class="sxs-lookup"><span data-stu-id="0627e-144">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="0627e-145">Pokud knihovnu vložené typy spolupráce ze <xref:Microsoft.Office.Interop.Excel> sestavení a zpřístupňuje je metoda, která vrací obecného typu, který má parametr, jehož typ <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, že metoda musí vracet obecné rozhraní, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0627e-145">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 <span data-ttu-id="0627e-146">V následujícím příkladu kódu klienta můžete volat metodu, která vrací <xref:System.Collections.IList> obecné rozhraní bez chyb.</span><span class="sxs-lookup"><span data-stu-id="0627e-146">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="0627e-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="0627e-147">Example</span></span>  
 <span data-ttu-id="0627e-148">Následující příkaz zkompiluje zdrojový soubor `OfficeApp.vb` a odkaz na sestavení z `COMData1.dll` a `COMData2.dll` k vytvoření `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="0627e-148">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0627e-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="0627e-149">See Also</span></span>  
 [<span data-ttu-id="0627e-150">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0627e-150">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0627e-151">Návod: Vložení typů ze spravovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="0627e-151">Walkthrough: Embedding Types from Managed Assemblies</span></span>](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="0627e-152">– referenční dokumentace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0627e-152">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="0627e-153">-noconfig</span><span class="sxs-lookup"><span data-stu-id="0627e-153">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="0627e-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="0627e-154">-libpath</span></span>](../../../visual-basic/reference/command-line-compiler/libpath.md)  
 [<span data-ttu-id="0627e-155">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0627e-155">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="0627e-156">Představení zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="0627e-156">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
