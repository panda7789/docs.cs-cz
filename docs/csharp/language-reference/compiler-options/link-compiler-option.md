---
title: -Link (C# možnosti kompilátoru)
ms.date: 07/20/2015
helpviewer_keywords:
- /l compiler option [C#]
- /link compiler option [C#]
- -l compiler option [C#]
- EmbedInteropTypes
- l compiler option [C#]
- embed interop types [COM Interop]
- -link compiler option [C#]
- link compiler option [C#]
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
ms.openlocfilehash: 724a848d4c31b2c4f6fc3427d70fc84f4fd944c6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924765"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="b0589-102">-Link (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="b0589-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="b0589-103">Způsobí, že kompilátor zpřístupní informace o typu COM v zadaných sestaveních pro projekt, který právě kompilujete.</span><span class="sxs-lookup"><span data-stu-id="b0589-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0589-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0589-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="b0589-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b0589-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="b0589-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b0589-106">Required.</span></span> <span data-ttu-id="b0589-107">Seznam názvů souborů sestavení oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="b0589-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="b0589-108">Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="b0589-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0589-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0589-109">Remarks</span></span>  
 <span data-ttu-id="b0589-110">`-link` Možnost umožňuje nasadit aplikaci, která obsahuje informace o vloženém typu.</span><span class="sxs-lookup"><span data-stu-id="b0589-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="b0589-111">Aplikace pak může použít typy v sestavení modulu runtime, které implementuje vložené informace o typu bez nutnosti odkazování na sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b0589-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="b0589-112">Pokud jsou publikovány různé verze sestavení modulu runtime, aplikace, která obsahuje informace o vloženém typu, může pracovat s různými verzemi, aniž by bylo nutné je znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="b0589-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="b0589-113">Příklad najdete v tématu [Návod: Vložení typů ze spravovaných sestavení](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="b0589-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="b0589-114">`-link` Použití možnosti je zvlášť užitečné, když pracujete se zprostředkovatelem komunikace s objekty com.</span><span class="sxs-lookup"><span data-stu-id="b0589-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="b0589-115">Můžete vložit typy modelu COM, aby již aplikace nevyžadovala primární definiční sestavení (PIA) v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="b0589-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="b0589-116">`-link` Možnost instruuje kompilátor, aby vložil informace o typu modelu COM z odkazovaného definičního sestavení do výsledného zkompilovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="b0589-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="b0589-117">Typ COM je identifikovaný hodnotou CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="b0589-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="b0589-118">V důsledku toho může být aplikace spuštěna na cílovém počítači, který má nainstalované stejné typy COM se stejnými hodnotami CLSID.</span><span class="sxs-lookup"><span data-stu-id="b0589-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="b0589-119">Dobrým příkladem jsou aplikace, které automatizují systém Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="b0589-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="b0589-120">Vzhledem k tomu, že aplikace, jako je například Office, obvykle udržují stejnou hodnotu CLSID napříč různými verzemi, může vaše aplikace používat odkazované typy COM, pokud je v cílovém počítači nainstalováno .NET Framework 4 nebo novější a vaše aplikace používá metody, vlastnosti nebo události, které jsou zahrnuty v odkazovaných typech COM.</span><span class="sxs-lookup"><span data-stu-id="b0589-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="b0589-121">`-link` Možnost vloží pouze rozhraní, struktury a delegáty.</span><span class="sxs-lookup"><span data-stu-id="b0589-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="b0589-122">Vkládání tříd modelu COM není podporováno.</span><span class="sxs-lookup"><span data-stu-id="b0589-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0589-123">Při vytváření instance vloženého typu modelu COM v kódu, je nutné vytvořit instanci pomocí příslušného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b0589-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="b0589-124">Při pokusu o vytvoření instance vloženého typu modelu COM pomocí třídy coclass dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="b0589-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="b0589-125">Chcete-li `-link` nastavit možnost v aplikaci Visual Studio, přidejte odkaz na sestavení a `Embed Interop Types` nastavte vlastnost na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="b0589-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="b0589-126">Výchozí hodnota `Embed Interop Types` vlastnosti je **false**.</span><span class="sxs-lookup"><span data-stu-id="b0589-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="b0589-127">Pokud propojíte se sestavením COM (sestavení A), které odkazuje na jiné sestavení COM (sestavení B), musíte také propojit se sestavením B, pokud je splněna jedna z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="b0589-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="b0589-128">Typ ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="b0589-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="b0589-129">Je vyvoláno pole, vlastnost, událost nebo metoda, které mají návratový typ nebo typ parametru ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="b0589-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="b0589-130">Podobně jako u možnosti `-link` kompilátoru [-reference](./reference-compiler-option.md) používá možnost kompilátoru soubor odpovědí CSc. rsp, který odkazuje na často používané .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="b0589-130">Like the [-reference](./reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="b0589-131">Pokud nechcete, aby kompilátor používal soubor csc. rsp, použijte možnost kompilátoru [--config](./noconfig-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="b0589-131">Use the [-noconfig](./noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="b0589-132">Krátká forma `-link` je `-l`.</span><span class="sxs-lookup"><span data-stu-id="b0589-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="b0589-133">Obecné typy a vložené typy</span><span class="sxs-lookup"><span data-stu-id="b0589-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="b0589-134">V následujících částech jsou popsána omezení používání obecných typů v aplikacích, které vkládají typy spolupráce.</span><span class="sxs-lookup"><span data-stu-id="b0589-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="b0589-135">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0589-135">Generic Interfaces</span></span>  
 <span data-ttu-id="b0589-136">Obecná rozhraní, která jsou vložena ze sestavení interop, nelze použít.</span><span class="sxs-lookup"><span data-stu-id="b0589-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="b0589-137">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b0589-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="b0589-138">Typy, které mají obecné parametry</span><span class="sxs-lookup"><span data-stu-id="b0589-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="b0589-139">Typy, které mají obecný parametr, jehož typ je vložený ze sestavení vzájemné spolupráce, se nedají použít, pokud je tento typ z externího sestavení.</span><span class="sxs-lookup"><span data-stu-id="b0589-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="b0589-140">Toto omezení se nevztahuje na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b0589-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="b0589-141">Zvažte <xref:Microsoft.Office.Interop.Excel.Range> například rozhraní, které je definováno <xref:Microsoft.Office.Interop.Excel> v sestavení.</span><span class="sxs-lookup"><span data-stu-id="b0589-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="b0589-142">Pokud knihovna vloží typy spolupráce ze <xref:Microsoft.Office.Interop.Excel> sestavení a zpřístupní metodu, která vrátí obecný typ s parametrem, jehož typ <xref:Microsoft.Office.Interop.Excel.Range> je rozhraní, musí tato metoda vracet obecné rozhraní, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="b0589-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#2)]  
[!code-csharp[VbLinkCompilerCS#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#3)]  
[!code-csharp[VbLinkCompilerCS#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#4)]  
  
 <span data-ttu-id="b0589-143">V následujícím příkladu kód klienta může zavolat metodu, která vrátí <xref:System.Collections.IList> obecné rozhraní bez chyby.</span><span class="sxs-lookup"><span data-stu-id="b0589-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]  
  
## <a name="example"></a><span data-ttu-id="b0589-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0589-144">Example</span></span>  
 <span data-ttu-id="b0589-145">Následující kód `OfficeApp.cs` zkompiluje zdrojový soubor a odkazuje na sestavení z `COMData1.dll` a `COMData2.dll` na `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="b0589-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0589-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0589-146">See also</span></span>

- [<span data-ttu-id="b0589-147">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b0589-147">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b0589-148">Návod: Vložení typů ze spravovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="b0589-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="b0589-149">-Reference (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="b0589-149">-reference (C# Compiler Options)</span></span>](./reference-compiler-option.md)
- [<span data-ttu-id="b0589-150">-unconfig (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="b0589-150">-noconfig (C# Compiler Options)</span></span>](./noconfig-compiler-option.md)
- [<span data-ttu-id="b0589-151">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="b0589-151">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
- [<span data-ttu-id="b0589-152">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="b0589-152">Interoperability Overview</span></span>](../../programming-guide/interop/interoperability-overview.md)
