---
title: -Link (Visual Basic)
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
ms.openlocfilehash: fbce22755b3732896a226c00bbf8e068dc1f098e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929400"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="81e73-102">-Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81e73-102">-link (Visual Basic)</span></span>
<span data-ttu-id="81e73-103">Způsobí, že kompilátor zpřístupní informace o typu COM v zadaných sestaveních pro projekt, který právě kompilujete.</span><span class="sxs-lookup"><span data-stu-id="81e73-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81e73-104">Syntax</span></span>  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="81e73-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="81e73-105">Arguments</span></span>  
  
|<span data-ttu-id="81e73-106">Termín</span><span class="sxs-lookup"><span data-stu-id="81e73-106">Term</span></span>|<span data-ttu-id="81e73-107">Definice</span><span class="sxs-lookup"><span data-stu-id="81e73-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="81e73-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="81e73-108">Required.</span></span> <span data-ttu-id="81e73-109">Seznam názvů souborů sestavení oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="81e73-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="81e73-110">Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="81e73-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81e73-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81e73-111">Remarks</span></span>  
 <span data-ttu-id="81e73-112">`-link` Možnost umožňuje nasadit aplikaci, která obsahuje informace o vloženém typu.</span><span class="sxs-lookup"><span data-stu-id="81e73-112">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="81e73-113">Aplikace pak může použít typy v sestavení modulu runtime, které implementuje vložené informace o typu bez nutnosti odkazování na sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="81e73-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="81e73-114">Pokud jsou publikovány různé verze sestavení modulu runtime, aplikace, která obsahuje informace o vloženém typu, může pracovat s různými verzemi, aniž by bylo nutné je znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="81e73-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="81e73-115">Příklad najdete v tématu [Návod: Vložení typů ze spravovaných sestavení](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="81e73-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span></span>  
  
 <span data-ttu-id="81e73-116">`-link` Použití možnosti je zvlášť užitečné, když pracujete se zprostředkovatelem komunikace s objekty com.</span><span class="sxs-lookup"><span data-stu-id="81e73-116">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="81e73-117">Můžete vložit typy modelu COM, aby již aplikace nevyžadovala primární definiční sestavení (PIA) v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="81e73-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="81e73-118">`-link` Možnost instruuje kompilátor, aby vložil informace o typu modelu COM z odkazovaného definičního sestavení do výsledného zkompilovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="81e73-118">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="81e73-119">Typ COM je identifikovaný hodnotou CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="81e73-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="81e73-120">V důsledku toho může být aplikace spuštěna na cílovém počítači, který má nainstalované stejné typy COM se stejnými hodnotami CLSID.</span><span class="sxs-lookup"><span data-stu-id="81e73-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="81e73-121">Dobrým příkladem jsou aplikace, které automatizují systém Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="81e73-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="81e73-122">Vzhledem k tomu, že aplikace, jako je například Office, obvykle udržují stejnou hodnotu CLSID napříč různými verzemi, může vaše aplikace používat odkazované typy COM, pokud je v cílovém počítači nainstalováno .NET Framework 4 nebo novější a vaše aplikace používá metody, vlastnosti nebo události, které jsou zahrnuty v odkazovaných typech COM.</span><span class="sxs-lookup"><span data-stu-id="81e73-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="81e73-123">`-link` Možnost vloží pouze rozhraní, struktury a delegáty.</span><span class="sxs-lookup"><span data-stu-id="81e73-123">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="81e73-124">Vkládání tříd modelu COM není podporováno.</span><span class="sxs-lookup"><span data-stu-id="81e73-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81e73-125">Při vytváření instance vloženého typu modelu COM v kódu, je nutné vytvořit instanci pomocí příslušného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81e73-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="81e73-126">Při pokusu o vytvoření instance vloženého typu modelu COM pomocí třídy coclass dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="81e73-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="81e73-127">Chcete-li `-link` nastavit možnost v aplikaci Visual Studio, přidejte odkaz na sestavení a `Embed Interop Types` nastavte vlastnost na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="81e73-127">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="81e73-128">Výchozí hodnota `Embed Interop Types` vlastnosti je **false**.</span><span class="sxs-lookup"><span data-stu-id="81e73-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="81e73-129">Pokud propojíte se sestavením COM (sestavení A), které odkazuje na jiné sestavení COM (sestavení B), musíte také propojit se sestavením B, pokud je splněna jedna z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="81e73-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="81e73-130">Typ ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="81e73-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="81e73-131">Je vyvoláno pole, vlastnost, událost nebo metoda, které mají návratový typ nebo typ parametru ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="81e73-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="81e73-132">Pomocí [-LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) Určete adresář, ve kterém je umístěn jeden nebo více odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="81e73-132">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="81e73-133">Podobně jako [](../../../visual-basic/reference/command-line-compiler/reference.md) možnost `-link` kompilátoru/reference používá možnost kompilátoru soubor odpovědí Vbc. rsp, který odkazuje na často používané .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="81e73-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="81e73-134">Pokud nechcete, aby kompilátor používal soubor Vbc. rsp, použijte možnost kompilátoru [--config](../../../visual-basic/reference/command-line-compiler/noconfig.md) .</span><span class="sxs-lookup"><span data-stu-id="81e73-134">Use the [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="81e73-135">Krátká forma `-link` je `-l`.</span><span class="sxs-lookup"><span data-stu-id="81e73-135">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="81e73-136">Obecné typy a vložené typy</span><span class="sxs-lookup"><span data-stu-id="81e73-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="81e73-137">V následujících částech jsou popsána omezení používání obecných typů v aplikacích, které vkládají typy spolupráce.</span><span class="sxs-lookup"><span data-stu-id="81e73-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="81e73-138">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="81e73-138">Generic Interfaces</span></span>  
 <span data-ttu-id="81e73-139">Obecná rozhraní, která jsou vložena ze sestavení interop, nelze použít.</span><span class="sxs-lookup"><span data-stu-id="81e73-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="81e73-140">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="81e73-140">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="81e73-141">Typy, které mají obecné parametry</span><span class="sxs-lookup"><span data-stu-id="81e73-141">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="81e73-142">Typy, které mají obecný parametr, jehož typ je vložený ze sestavení vzájemné spolupráce, se nedají použít, pokud je tento typ z externího sestavení.</span><span class="sxs-lookup"><span data-stu-id="81e73-142">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="81e73-143">Toto omezení se nevztahuje na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81e73-143">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="81e73-144">Zvažte <xref:Microsoft.Office.Interop.Excel.Range> například rozhraní, které je definováno <xref:Microsoft.Office.Interop.Excel> v sestavení.</span><span class="sxs-lookup"><span data-stu-id="81e73-144">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="81e73-145">Pokud knihovna vloží typy spolupráce ze <xref:Microsoft.Office.Interop.Excel> sestavení a zpřístupní metodu, která vrátí obecný typ s parametrem, jehož typ <xref:Microsoft.Office.Interop.Excel.Range> je rozhraní, musí tato metoda vracet obecné rozhraní, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="81e73-145">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="81e73-146">V následujícím příkladu kód klienta může zavolat metodu, která vrátí <xref:System.Collections.IList> obecné rozhraní bez chyby.</span><span class="sxs-lookup"><span data-stu-id="81e73-146">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="81e73-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="81e73-147">Example</span></span>  
 <span data-ttu-id="81e73-148">Následující příkazový řádek zkompiluje zdrojový `OfficeApp.vb` soubor a referenční sestavení z `COMData1.dll` a `COMData2.dll` do `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="81e73-148">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="81e73-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81e73-149">See also</span></span>

- [<span data-ttu-id="81e73-150">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="81e73-150">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="81e73-151">Návod: Vložení typů ze spravovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="81e73-151">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="81e73-152">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81e73-152">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="81e73-153">-noconfig</span><span class="sxs-lookup"><span data-stu-id="81e73-153">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="81e73-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="81e73-154">-libpath</span></span>](../../../visual-basic/reference/command-line-compiler/libpath.md)
- [<span data-ttu-id="81e73-155">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="81e73-155">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="81e73-156">Představení zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="81e73-156">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
