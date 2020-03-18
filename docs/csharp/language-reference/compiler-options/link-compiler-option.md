---
title: -link (Možnosti kompilátoru Jazyka C#)
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
ms.openlocfilehash: 4c96f7be5ac500886ea036c93b4651fa814ee58a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970098"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="4b2be-102">-link (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4b2be-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="4b2be-103">Způsobí, že kompilátor zpřístupnit informace o typu COM v zadaných sestaveních projektu, který právě kompilujete.</span><span class="sxs-lookup"><span data-stu-id="4b2be-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b2be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b2be-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b2be-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4b2be-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="4b2be-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="4b2be-106">Required.</span></span> <span data-ttu-id="4b2be-107">Seznam názvů souborů sestavení oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="4b2be-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="4b2be-108">Pokud název souboru obsahuje mezeru, uzavřete jej do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="4b2be-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b2be-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b2be-109">Remarks</span></span>  
 <span data-ttu-id="4b2be-110">Tato `-link` možnost umožňuje nasadit aplikaci, která má vložené informace o typu.</span><span class="sxs-lookup"><span data-stu-id="4b2be-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="4b2be-111">Aplikace pak můžete použít typy v sestavení za běhu, které implementují informace o vloženém typu bez nutnosti odkazu na sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="4b2be-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="4b2be-112">Pokud jsou publikovány různé verze sestavení runtime, aplikace, která obsahuje informace o vloženém typu, může pracovat s různými verzemi, aniž by bylo nutné je znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="4b2be-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="4b2be-113">Příklad najdete [v tématu Návod: Vkládání typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="4b2be-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="4b2be-114">Použití `-link` této možnosti je užitečné zejména při práci s komop.</span><span class="sxs-lookup"><span data-stu-id="4b2be-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="4b2be-115">Typy COM můžete vložit tak, aby aplikace již nevyžadovala primární sestavení interop (PIA) v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="4b2be-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="4b2be-116">Tato `-link` možnost instruuje kompilátor vložit informace o typu COM z odkazované ho sestavení interop do výsledného kompilovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="4b2be-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="4b2be-117">Typ COM je identifikován hodnotou CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="4b2be-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="4b2be-118">V důsledku toho může být aplikace spuštěna v cílovém počítači, který nainstaloval stejné typy COM se stejnými hodnotami CLSID.</span><span class="sxs-lookup"><span data-stu-id="4b2be-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="4b2be-119">Dobrým příkladem jsou aplikace, které automatizují sadu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="4b2be-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="4b2be-120">Vzhledem k tomu, že aplikace, jako je Office, obvykle zachovávaly stejnou hodnotu CLSID v různých verzích, může aplikace používat odkazované typy COM, pokud je v cílovém počítači nainstalována rozhraní .NET Framework 4 nebo novější a aplikace používá metody, vlastnosti nebo události, které jsou zahrnuty v odkazovaných typech COM.</span><span class="sxs-lookup"><span data-stu-id="4b2be-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="4b2be-121">Možnost `-link` vloží pouze rozhraní, struktury a delegáty.</span><span class="sxs-lookup"><span data-stu-id="4b2be-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="4b2be-122">Vkládání tříd COM není podporováno.</span><span class="sxs-lookup"><span data-stu-id="4b2be-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b2be-123">Při vytváření instance vloženého typu COM v kódu je nutné vytvořit instanci pomocí příslušného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4b2be-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="4b2be-124">Pokus o vytvoření instance vloženého typu COM pomocí třídy CoClass způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="4b2be-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="4b2be-125">Chcete-li `-link` nastavit možnost v sadě Visual Studio, přidejte odkaz na sestavení a nastavte vlastnost na `Embed Interop Types` **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="4b2be-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="4b2be-126">Výchozí hodnota `Embed Interop Types` vlastnosti je **false**.</span><span class="sxs-lookup"><span data-stu-id="4b2be-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="4b2be-127">Pokud propojíte sestavení COM (sestavení A), které samo odkazuje na jiné sestavení COM (sestavení B), musíte také propojit se sestavením B, pokud platí některá z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="4b2be-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="4b2be-128">Typ z sestavení A dědí z typu nebo implementuje rozhraní z sestavení B.</span><span class="sxs-lookup"><span data-stu-id="4b2be-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="4b2be-129">Pole, vlastnost, událost nebo metoda, která má návratový typ nebo typ parametru z sestavení B je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="4b2be-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="4b2be-130">Stejně jako možnost kompilátoru `-link` [-reference](./reference-compiler-option.md) používá možnost kompilátoru soubor odpovědí Csc.rsp, který odkazuje na často používaná sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b2be-130">Like the [-reference](./reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="4b2be-131">Pokud nechcete, aby kompilátor používal soubor Csc.rsp, použijte možnost kompilátoru [-noconfig.](./noconfig-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="4b2be-131">Use the [-noconfig](./noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="4b2be-132">Krátká forma `-link` je `-l`.</span><span class="sxs-lookup"><span data-stu-id="4b2be-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="4b2be-133">Obecné typy a vložené typy</span><span class="sxs-lookup"><span data-stu-id="4b2be-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="4b2be-134">Následující části popisují omezení používání obecných typů v aplikacích, které vkládají typy interop.</span><span class="sxs-lookup"><span data-stu-id="4b2be-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="4b2be-135">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b2be-135">Generic Interfaces</span></span>  
 <span data-ttu-id="4b2be-136">Obecná rozhraní, která jsou vložena z interop sestavení nelze použít.</span><span class="sxs-lookup"><span data-stu-id="4b2be-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="4b2be-137">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4b2be-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="4b2be-138">Typy, které mají obecné parametry</span><span class="sxs-lookup"><span data-stu-id="4b2be-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="4b2be-139">Typy, které mají obecný parametr, jehož typ je vložen z interop sestavení nelze použít, pokud tento typ je z externího sestavení.</span><span class="sxs-lookup"><span data-stu-id="4b2be-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="4b2be-140">Toto omezení se nevztahuje na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4b2be-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="4b2be-141">Zvažte například <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, které <xref:Microsoft.Office.Interop.Excel> je definováno v sestavení.</span><span class="sxs-lookup"><span data-stu-id="4b2be-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="4b2be-142">Pokud knihovna vloží interop <xref:Microsoft.Office.Interop.Excel> typy z sestavení a zpřístupní metodu, která vrací <xref:Microsoft.Office.Interop.Excel.Range> obecný typ, který má parametr, jehož typ je rozhraní, tato metoda musí vrátit obecné rozhraní, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="4b2be-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#2)]  
[!code-csharp[VbLinkCompilerCS#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#3)]  
[!code-csharp[VbLinkCompilerCS#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#4)]  
  
 <span data-ttu-id="4b2be-143">V následujícím příkladu může klientský kód <xref:System.Collections.IList> volat metodu, která vrací obecné rozhraní bez chyby.</span><span class="sxs-lookup"><span data-stu-id="4b2be-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]  
  
## <a name="example"></a><span data-ttu-id="4b2be-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b2be-144">Example</span></span>  
 <span data-ttu-id="4b2be-145">Následující kód zkompiluje zdrojový `OfficeApp.cs` soubor a referenční sestavení z `COMData1.dll` a `COMData2.dll` k vytvoření `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="4b2be-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b2be-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b2be-146">See also</span></span>

- [<span data-ttu-id="4b2be-147">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4b2be-147">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4b2be-148">Návod: Vložení typů ze spravovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="4b2be-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="4b2be-149">-reference (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4b2be-149">-reference (C# Compiler Options)</span></span>](./reference-compiler-option.md)
- [<span data-ttu-id="4b2be-150">-noconfig (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4b2be-150">-noconfig (C# Compiler Options)</span></span>](./noconfig-compiler-option.md)
- [<span data-ttu-id="4b2be-151">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="4b2be-151">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
- [<span data-ttu-id="4b2be-152">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="4b2be-152">Interoperability Overview</span></span>](../../programming-guide/interop/interoperability-overview.md)
