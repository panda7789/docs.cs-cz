---
title: -link
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
ms.openlocfilehash: ecb7b0448b8ee9c1c1fc1eb9542b693d60a38ffd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335852"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="0b9eb-102">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b9eb-102">-link (Visual Basic)</span></span>
<span data-ttu-id="0b9eb-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b9eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b9eb-104">Syntax</span></span>  
  
```console  
-link:fileList  
```

<span data-ttu-id="0b9eb-105">or</span><span class="sxs-lookup"><span data-stu-id="0b9eb-105">or</span></span>  

```console
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b9eb-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="0b9eb-106">Arguments</span></span>  
  
|<span data-ttu-id="0b9eb-107">Termín</span><span class="sxs-lookup"><span data-stu-id="0b9eb-107">Term</span></span>|<span data-ttu-id="0b9eb-108">Definice</span><span class="sxs-lookup"><span data-stu-id="0b9eb-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="0b9eb-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-109">Required.</span></span> <span data-ttu-id="0b9eb-110">Comma-delimited list of assembly file names.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="0b9eb-111">If the file name contains a space, enclose the name in quotation marks.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b9eb-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b9eb-112">Remarks</span></span>  
 <span data-ttu-id="0b9eb-113">The `-link` option enables you to deploy an application that has embedded type information.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-113">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="0b9eb-114">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-114">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="0b9eb-115">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-115">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="0b9eb-116">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="0b9eb-116">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="0b9eb-117">Using the `-link` option is especially useful when you are working with COM interop.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-117">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="0b9eb-118">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-118">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="0b9eb-119">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-119">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="0b9eb-120">The COM type is identified by the CLSID (GUID) value.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-120">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="0b9eb-121">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-121">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="0b9eb-122">Applications that automate Microsoft Office are a good example.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-122">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="0b9eb-123">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-123">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="0b9eb-124">The `-link` option embeds only interfaces, structures, and delegates.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-124">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="0b9eb-125">Embedding COM classes is not supported.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-125">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b9eb-126">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-126">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="0b9eb-127">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-127">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="0b9eb-128">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-128">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="0b9eb-129">The default for the `Embed Interop Types` property is **false**.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-129">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="0b9eb-130">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span><span class="sxs-lookup"><span data-stu-id="0b9eb-130">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="0b9eb-131">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-131">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="0b9eb-132">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-132">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="0b9eb-133">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-133">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="0b9eb-134">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-134">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="0b9eb-135">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-135">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="0b9eb-136">The short form of `-link` is `-l`.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-136">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="0b9eb-137">Generics and Embedded Types</span><span class="sxs-lookup"><span data-stu-id="0b9eb-137">Generics and Embedded Types</span></span>  
 <span data-ttu-id="0b9eb-138">The following sections describe the limitations on using generic types in applications that embed interop types.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-138">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="0b9eb-139">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b9eb-139">Generic Interfaces</span></span>  
 <span data-ttu-id="0b9eb-140">Generic interfaces that are embedded from an interop assembly cannot be used.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-140">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="0b9eb-141">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-141">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="0b9eb-142">Types That Have Generic Parameters</span><span class="sxs-lookup"><span data-stu-id="0b9eb-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="0b9eb-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="0b9eb-144">This restriction does not apply to interfaces.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="0b9eb-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="0b9eb-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="0b9eb-147">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-147">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="0b9eb-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b9eb-148">Example</span></span>  
 <span data-ttu-id="0b9eb-149">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="0b9eb-149">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b9eb-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b9eb-150">See also</span></span>

- [<span data-ttu-id="0b9eb-151">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="0b9eb-151">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0b9eb-152">Návod: Vložení typů ze spravovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="0b9eb-152">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="0b9eb-153">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b9eb-153">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="0b9eb-154">-noconfig</span><span class="sxs-lookup"><span data-stu-id="0b9eb-154">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="0b9eb-155">-libpath</span><span class="sxs-lookup"><span data-stu-id="0b9eb-155">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="0b9eb-156">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0b9eb-156">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="0b9eb-157">Představení zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="0b9eb-157">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
