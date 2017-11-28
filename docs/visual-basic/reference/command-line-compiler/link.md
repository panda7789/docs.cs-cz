---
title: /link (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: effaeae48bdeb1dfd0f8cda31fedf2436e7deaca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="link-visual-basic"></a><span data-ttu-id="fab89-102">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fab89-102">/link (Visual Basic)</span></span>
<span data-ttu-id="fab89-103">Způsobí, že kompilátor pro zpřístupnění informací o typu modelu COM v zadaném sestavení pro projekt, který je aktuálně kompilován.</span><span class="sxs-lookup"><span data-stu-id="fab89-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fab89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fab89-104">Syntax</span></span>  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="fab89-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fab89-105">Arguments</span></span>  
  
|<span data-ttu-id="fab89-106">Termín</span><span class="sxs-lookup"><span data-stu-id="fab89-106">Term</span></span>|<span data-ttu-id="fab89-107">Definice</span><span class="sxs-lookup"><span data-stu-id="fab89-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="fab89-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fab89-108">Required.</span></span> <span data-ttu-id="fab89-109">Čárkami oddělený seznam názvů souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="fab89-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="fab89-110">Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="fab89-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fab89-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fab89-111">Remarks</span></span>  
 <span data-ttu-id="fab89-112">`/link` Možnost umožňuje nasadit aplikaci, která obsahuje vložené informace o typu.</span><span class="sxs-lookup"><span data-stu-id="fab89-112">The `/link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="fab89-113">Aplikace pak můžete použít typy v sestavení modulu runtime, které implementují vložené typové informace bez nutnosti odkaz na sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="fab89-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="fab89-114">Pokud jsou publikovány v různých verzích sestavení modulu runtime, můžete aplikaci, která obsahuje informace o vložených typu pracovat s různými verzemi bez nutnosti zopakovat.</span><span class="sxs-lookup"><span data-stu-id="fab89-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="fab89-115">Příklad, naleznete v části [návod: vložení typů ze spravovaných sestavení](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="fab89-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="fab89-116">Pomocí `/link` možnost je obzvláště užitečná při práci se zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="fab89-116">Using the `/link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="fab89-117">Můžete vložit typy modelu COM, tak, aby vaše aplikace vyžaduje již primární spolupracující sestavení (PIA) na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="fab89-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="fab89-118">`/link` Možnost dává pokyn kompilátoru pro vložení informací o typu modelu COM z odkazovaného definičního sestavení do výsledného zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="fab89-118">The `/link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="fab89-119">Typ modelu COM je identifikována hodnota CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="fab89-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="fab89-120">V důsledku toho lze aplikaci spustit v cílovém počítači, který má nainstalován stejné typy modelu COM pomocí stejné hodnoty CLSID.</span><span class="sxs-lookup"><span data-stu-id="fab89-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="fab89-121">Dobrým příkladem jsou aplikace, které automatizují Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="fab89-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="fab89-122">Vzhledem k tomu, že aplikace, jako je Office obvykle zachovat stejnou hodnotu CLSID mezi různými verzemi, vaše aplikace může použít odkazované typy modelu COM, jak dlouho jako rozhraní .NET Framework 4 nebo novější je nainstalován v cílovém počítači a vaše aplikace používá metody, vlastnosti, nebo události, které jsou součástí odkazované typy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="fab89-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="fab89-123">`/link` Možnost vloží pouze rozhraní, struktur a delegáti.</span><span class="sxs-lookup"><span data-stu-id="fab89-123">The `/link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="fab89-124">Vložení třídy COM není podporována.</span><span class="sxs-lookup"><span data-stu-id="fab89-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fab89-125">Když vytvoříte instanci vloženého typu modelu COM v kódu, musíte vytvořit instanci pomocí odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fab89-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="fab89-126">Při pokusu o vytvoření instance vloženého typu modelu COM pomocí CoClass způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="fab89-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="fab89-127">Chcete-li nastavit `/link` možnost v [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], přidejte odkaz na sestavení a nastavte `Embed Interop Types` vlastnost, která má **true**.</span><span class="sxs-lookup"><span data-stu-id="fab89-127">To set the `/link` option in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="fab89-128">Výchozí hodnota pro `Embed Interop Types` vlastnost je **false**.</span><span class="sxs-lookup"><span data-stu-id="fab89-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="fab89-129">Pokud jste k sestavení modelu COM (sestavení A) které se odkazuje na jiný sestavení modelu COM (sestavení B), budete také muset propojit sestavení B, pokud platí některá z následujících:</span><span class="sxs-lookup"><span data-stu-id="fab89-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="fab89-130">Typu ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="fab89-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="fab89-131">Pole, vlastnost, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B je volána.</span><span class="sxs-lookup"><span data-stu-id="fab89-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="fab89-132">Použití [/Libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) na adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="fab89-132">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="fab89-133">Jako [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) – možnost kompilátoru, `/link` používá soubor odpovědí Vbc.rsp, často používanou odkazy [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="fab89-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `/link` compiler option uses the Vbc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="fab89-134">Použít [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) – možnost kompilátoru Pokud nechcete, aby kompilátoru chcete použít soubor Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="fab89-134">Use the [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="fab89-135">Zkratka pro `/link` je `/l`.</span><span class="sxs-lookup"><span data-stu-id="fab89-135">The short form of `/link` is `/l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="fab89-136">Obecné typy a vložené typy.</span><span class="sxs-lookup"><span data-stu-id="fab89-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="fab89-137">Následující části popisují omezení na použití obecných typů v aplikacích, které přibalit definované typy.</span><span class="sxs-lookup"><span data-stu-id="fab89-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="fab89-138">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="fab89-138">Generic Interfaces</span></span>  
 <span data-ttu-id="fab89-139">Obecná rozhraní, které jsou vloženy z definičního sestavení nelze použít.</span><span class="sxs-lookup"><span data-stu-id="fab89-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="fab89-140">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fab89-140">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="fab89-141">Typy, které mají obecné parametry</span><span class="sxs-lookup"><span data-stu-id="fab89-141">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="fab89-142">Typy, které mají obecný parametr, jehož typ je vložen z definičního sestavení nelze použít, pokud je tento typ z externího sestavení.</span><span class="sxs-lookup"><span data-stu-id="fab89-142">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="fab89-143">Toto omezení se nevztahuje na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fab89-143">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="fab89-144">Představte si třeba <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, která je definována v <xref:Microsoft.Office.Interop.Excel> sestavení.</span><span class="sxs-lookup"><span data-stu-id="fab89-144">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="fab89-145">Pokud knihovna vkládá typy spolupráce z <xref:Microsoft.Office.Interop.Excel> sestavení a zpřístupňuje je metoda, která vrátí obecný typ, který má parametr, jehož typ <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, že metoda musí vracet generické rozhraní, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="fab89-145">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 <span data-ttu-id="fab89-146">V následujícím příkladu kódu klienta můžete volat metodu, která vrátí <xref:System.Collections.IList> obecné rozhraní bez chyby.</span><span class="sxs-lookup"><span data-stu-id="fab89-146">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="fab89-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="fab89-147">Example</span></span>  
 <span data-ttu-id="fab89-148">Následující kód zkompiluje zdrojový soubor `OfficeApp.vb` a odkaz na sestavení z `COMData1.dll` a `COMData2.dll` k vytvoření `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="fab89-148">The following code compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```vb  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fab89-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="fab89-149">See Also</span></span>  
 [<span data-ttu-id="fab89-150">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="fab89-150">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="fab89-151">Návod: Vložení typů z řízených sestavení</span><span class="sxs-lookup"><span data-stu-id="fab89-151">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="fab89-152">/ Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fab89-152">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="fab89-153">/ noconfig</span><span class="sxs-lookup"><span data-stu-id="fab89-153">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="fab89-154">/ Libpath</span><span class="sxs-lookup"><span data-stu-id="fab89-154">/libpath</span></span>](../../../visual-basic/reference/command-line-compiler/libpath.md)  
 [<span data-ttu-id="fab89-155">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="fab89-155">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="fab89-156">Úvod do zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="fab89-156">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
