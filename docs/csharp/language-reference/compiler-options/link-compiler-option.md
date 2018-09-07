---
title: -link (možnosti kompilátoru C#)
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
ms.openlocfilehash: 00cfda489feb468c7e3c140ab63369b408b09152
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44046314"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="8f6e2-102">-link (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="8f6e2-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="8f6e2-103">Způsobí, že kompilátor pro zpřístupnění informací o typu modelu COM v zadaném sestavení pro projekt, který je aktuálně kompilován.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f6e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f6e2-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="8f6e2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8f6e2-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="8f6e2-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-106">Required.</span></span> <span data-ttu-id="8f6e2-107">Čárkami oddělený seznam názvů souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="8f6e2-108">Pokud název souboru obsahuje mezery, uzavřete název do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f6e2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f6e2-109">Remarks</span></span>  
 <span data-ttu-id="8f6e2-110">`-link` Možnost můžete nasazovat aplikace, která obsahuje vložené informace o typu.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="8f6e2-111">Aplikace pak můžete použít typy v sestavení modulu runtime, které implementují informace o vloženém typu bez nutnosti odkaz na sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="8f6e2-112">Pokud různé verze sestavení modulu runtime jsou publikovány, aplikace, která obsahuje informace o vloženém typu můžete pracovat se různé verze, aniž byste museli být překompilovány.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="8f6e2-113">Příklad najdete v tématu [návod: vložení typů ze spravovaných sestavení](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="8f6e2-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="8f6e2-114">Použití `-link` volba je užitečná při práci se spoluprací COM.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="8f6e2-115">Můžete vložit typy modelu COM, tak, aby vaše aplikace vyžaduje již primární definiční sestavení (PIA) na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="8f6e2-116">`-link` Možnost dává pokyn kompilátoru k vložení informací o typu modelu COM z odkazované sestavení vzájemné spolupráce do výsledné zkompilovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="8f6e2-117">Typ modelu COM je identifikován hodnota CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="8f6e2-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="8f6e2-118">V důsledku toho může vaše aplikace spouštět na cílovém počítači, který má nainstalovanou stejné typy modelu COM se stejnými hodnotami identifikátoru CLSID.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="8f6e2-119">Dobrým příkladem jsou aplikace, které automatizují Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="8f6e2-120">Protože aplikace, jako je Office obvykle ponechat stejnou hodnotu CLSID napříč různými verzemi, aplikace může používat odkazované typy modelu COM v cílovém počítači je nainstalované rozhraní .NET Framework 4 nebo vyšší a vaše aplikace používá metody, vlastnosti, nebo události, které jsou zahrnuty v odkazovaných typů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="8f6e2-121">`-link` Možnost vloží pouze rozhraní, struktury a delegátů.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="8f6e2-122">Vložení třídy modelu COM není podporováno.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f6e2-123">Při vytváření instance vloženého typu modelu COM ve vašem kódu, musíte vytvořit instanci pomocí odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="8f6e2-124">Pokus o vytvoření instance vloženého typu modelu COM s použitím CoClass způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="8f6e2-125">Chcete-li nastavit `-link` v aplikaci Visual Studio, přidejte odkaz na sestavení a nastavte `Embed Interop Types` vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="8f6e2-126">Výchozí nastavení pro `Embed Interop Types` vlastnost **false**.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="8f6e2-127">Pokud jste se k sestavení modelu COM (sestavení A) která sama odkazuje na jiné sestavení modelu COM (sestavení B), budete mít taky odkaz na sestavení B, pokud je splněna jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="8f6e2-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="8f6e2-128">Typ v sestavení A je odvozen z typu nebo implementuje rozhraní ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="8f6e2-129">Pole, vlastnosti, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="8f6e2-130">Stejně jako [– referenční dokumentace](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) – možnost kompilátoru, `-link` – možnost kompilátoru používá Csc.rsp soubor odpovědí, který často používá odkazy [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-130">Like the [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="8f6e2-131">Použít [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Pokud nechcete, aby kompilátor, aby používal soubor Csc.rsp – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-131">Use the [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="8f6e2-132">Krátký tvar `-link` je `-l`.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="8f6e2-133">Obecných typů a vestavěné typy</span><span class="sxs-lookup"><span data-stu-id="8f6e2-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="8f6e2-134">Omezení týkající se použití obecných typů v aplikacích, které vložit typy spolupráce v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="8f6e2-135">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f6e2-135">Generic Interfaces</span></span>  
 <span data-ttu-id="8f6e2-136">Obecná rozhraní, které jsou vloženy z definičního sestavení nelze použít.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="8f6e2-137">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="8f6e2-138">Typy, které mají obecné parametry.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="8f6e2-139">Typy, které mají obecný parametr, jehož typ je vložen z definičního sestavení nelze použít, pokud je tento typ z externího sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="8f6e2-140">Toto omezení se nevztahuje na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="8f6e2-141">Představme si třeba, <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, která je definována v <xref:Microsoft.Office.Interop.Excel> sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="8f6e2-142">Pokud knihovnu vložené typy spolupráce ze <xref:Microsoft.Office.Interop.Excel> sestavení a zpřístupňuje je metoda, která vrací obecného typu, který má parametr, jehož typ <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, že metoda musí vracet obecné rozhraní, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 <span data-ttu-id="8f6e2-143">V následujícím příkladu kódu klienta můžete volat metodu, která vrací <xref:System.Collections.IList> obecné rozhraní bez chyb.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="8f6e2-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f6e2-144">Example</span></span>  
 <span data-ttu-id="8f6e2-145">Následující kód se zkompiluje zdrojový soubor `OfficeApp.cs` a odkaz na sestavení z `COMData1.dll` a `COMData2.dll` k vytvoření `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="8f6e2-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f6e2-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f6e2-146">See Also</span></span>

- [<span data-ttu-id="8f6e2-147">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8f6e2-147">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="8f6e2-148">Návod: Vložení typů ze spravovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="8f6e2-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [<span data-ttu-id="8f6e2-149">-reference (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="8f6e2-149">-reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)  
- [<span data-ttu-id="8f6e2-150">-noconfig (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="8f6e2-150">-noconfig (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)  
- [<span data-ttu-id="8f6e2-151">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="8f6e2-151">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [<span data-ttu-id="8f6e2-152">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="8f6e2-152">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)
