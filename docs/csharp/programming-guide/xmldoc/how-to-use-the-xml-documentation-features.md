---
title: "Postupy: Použití funkcí dokumentace XML (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb647a275a5cd5fac2316706591440d9792861b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="a2e9a-102">Postupy: Použití funkcí dokumentace XML (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a2e9a-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="a2e9a-103">Následující příklad obsahuje základní přehled typu, který byly dokumentovány.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2e9a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a2e9a-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 <span data-ttu-id="a2e9a-105">**Tento soubor .xml se vygeneroval s předchozí ukázka kódu.**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-105">**// This .xml file was generated with the previous code sample.**</span></span>  
<span data-ttu-id="a2e9a-106">**\<? xml verze = "1.0"? >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-106">**\<?xml version="1.0"?>**</span></span>  
<span data-ttu-id="a2e9a-107">**\<doc >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-107">**\<doc>**</span></span>  
 <span data-ttu-id="a2e9a-108">**\<sestavení >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-108">**\<assembly>**</span></span>  
 <span data-ttu-id="a2e9a-109">**\<název > xmlsample \< /name >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-109">**\<name>xmlsample\</name>**</span></span>  
 <span data-ttu-id="a2e9a-110">**\</Assembly >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-110">**\</assembly>**</span></span>  
 <span data-ttu-id="a2e9a-111">**\<členy >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-111">**\<members>**</span></span>  
 <span data-ttu-id="a2e9a-112">**\<Název člena = "T:SomeClass" >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-112">**\<member name="T:SomeClass">**</span></span>  
 <span data-ttu-id="a2e9a-113">**\<Souhrn >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-113">**\<summary>**</span></span>  
 <span data-ttu-id="a2e9a-114">**Sem zadejte třída úrovni souhrnu dokumentace. \<nebo souhrnných >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-114">**Class level summary documentation goes here.\</summary>**</span></span>  
 <span data-ttu-id="a2e9a-115">**\<Poznámky >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-115">**\<remarks>**</span></span>  
 <span data-ttu-id="a2e9a-116">**Může být přidružen typ nebo člen delší komentáře**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-116">**Longer comments can be associated with a type or member**</span></span>  
 <span data-ttu-id="a2e9a-117">**pomocí značky poznámky \< /remarks >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-117">**through the remarks tag\</remarks>**</span></span>  
 <span data-ttu-id="a2e9a-118">**\</member >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-118">**\</member>**</span></span>  
 <span data-ttu-id="a2e9a-119">**\<člen name="F:SomeClass.m_Name" >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-119">**\<member name="F:SomeClass.m_Name">**</span></span>  
 <span data-ttu-id="a2e9a-120">**\<Souhrn >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-120">**\<summary>**</span></span>  
 <span data-ttu-id="a2e9a-121">**Úložiště pro vlastnost název\<nebo souhrnných >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-121">**Store for the name property\</summary>**</span></span>  
 <span data-ttu-id="a2e9a-122">**\</member >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-122">**\</member>**</span></span>  
 <span data-ttu-id="a2e9a-123">**\<Název člena = "M:SomeClass. #ctor" >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-123">**\<member name="M:SomeClass.#ctor">**</span></span>  
 <span data-ttu-id="a2e9a-124">**\<Souhrn > konstruktoru třídy. \<nebo souhrnných >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-124">**\<summary>The class constructor.\</summary>**</span></span>  
 <span data-ttu-id="a2e9a-125">**\</member >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-125">**\</member>**</span></span>  
 <span data-ttu-id="a2e9a-126">**\<člen name="M:SomeClass.SomeMethod(System.String)" >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-126">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="a2e9a-127">**\<Souhrn >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-127">**\<summary>**</span></span>  
 <span data-ttu-id="a2e9a-128">**Popis SomeMethod. \<nebo souhrnných >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-128">**Description for SomeMethod.\</summary>**</span></span>  
 <span data-ttu-id="a2e9a-129">**\<Název parametru = "s" > zde bude parametr popis s\</param >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-129">**\<param name="s"> Parameter description for s goes here\</param>**</span></span>  
 <span data-ttu-id="a2e9a-130">**\<Viz také cref="T:System.String" >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-130">**\<seealso cref="T:System.String">**</span></span>  
 <span data-ttu-id="a2e9a-131">**Cref – atribut v libovolné značky můžete použít tak, aby odkazovaly na typ nebo člen**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-131">**You can use the cref attribute on any tag to reference a type or member**</span></span>  
 <span data-ttu-id="a2e9a-132">**a kompilátor zkontroluje, zda existuje odkaz na. \</seealso >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-132">**and the compiler will check that the reference exists. \</seealso>**</span></span>  
 <span data-ttu-id="a2e9a-133">**\</member >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-133">**\</member>**</span></span>  
 <span data-ttu-id="a2e9a-134">**\<člen name="M:SomeClass.SomeOtherMethod" >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-134">**\<member name="M:SomeClass.SomeOtherMethod">**</span></span>  
 <span data-ttu-id="a2e9a-135">**\<Souhrn >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-135">**\<summary>**</span></span>  
 <span data-ttu-id="a2e9a-136">**Jiné metody. \<nebo souhrnných >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-136">**Some other method. \</summary>**</span></span>  
 <span data-ttu-id="a2e9a-137">**\<Vrátí >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-137">**\<returns>**</span></span>  
 <span data-ttu-id="a2e9a-138">**Jsou vráceny výsledky popsané prostřednictvím vrátí značky.  \< /vrátí >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-138">**Return results are described through the returns tag.\</returns>**</span></span>  
 <span data-ttu-id="a2e9a-139">**\<Viz také cref="M:SomeClass.SomeMethod(System.String)" >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-139">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="a2e9a-140">**Všimněte si použití atributu cref – Chcete-li konkrétní metody \</seealso >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-140">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span></span>  
 <span data-ttu-id="a2e9a-141">**\</member >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-141">**\</member>**</span></span>  
 <span data-ttu-id="a2e9a-142">**\<člen name="M:SomeClass.Main(System.String[])" >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-142">**\<member name="M:SomeClass.Main(System.String[])">**</span></span>  
 <span data-ttu-id="a2e9a-143">**\<Souhrn >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-143">**\<summary>**</span></span>  
 <span data-ttu-id="a2e9a-144">**Vstupní bod pro aplikaci.**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-144">**The entry point for the application.**</span></span>  
 <span data-ttu-id="a2e9a-145">**\</ souhrnné >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-145">**\</summary>**</span></span>  
 <span data-ttu-id="a2e9a-146">**\<Název parametru = "argumentů" > seznam argumentů příkazového řádku\</param >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-146">**\<param name="args"> A list of command line arguments\</param>**</span></span>  
 <span data-ttu-id="a2e9a-147">**\</member >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-147">**\</member>**</span></span>  
 <span data-ttu-id="a2e9a-148">**\<člen name="P:SomeClass.Name" >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-148">**\<member name="P:SomeClass.Name">**</span></span>  
 <span data-ttu-id="a2e9a-149">**\<Souhrn >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-149">**\<summary>**</span></span>  
 <span data-ttu-id="a2e9a-150">**Name – vlastnost \<nebo souhrnných >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-150">**Name property \</summary>**</span></span>  
 <span data-ttu-id="a2e9a-151">**\<Hodnota >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-151">**\<value>**</span></span>  
 <span data-ttu-id="a2e9a-152">**Hodnota značky je používán k popisu hodnota vlastnosti \< /value >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-152">**A value tag is used to describe the property value\</value>**</span></span>  
 <span data-ttu-id="a2e9a-153">**\</member >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-153">**\</member>**</span></span>  
 <span data-ttu-id="a2e9a-154">**\</Members >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-154">**\</members>**</span></span>  
<span data-ttu-id="a2e9a-155">**\</ doc >**</span><span class="sxs-lookup"><span data-stu-id="a2e9a-155">**\</doc>**</span></span>   
## <a name="compiling-the-code"></a><span data-ttu-id="a2e9a-156">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a2e9a-156">Compiling the Code</span></span>  
 <span data-ttu-id="a2e9a-157">Kompilace v příkladu, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="a2e9a-157">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="a2e9a-158">Tím se vytvoří soubor XML XMLsample.xml, které lze zobrazit v prohlížeči nebo pomocí příkazu typu.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-158">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a2e9a-159">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="a2e9a-159">Robust Programming</span></span>  
 <span data-ttu-id="a2e9a-160">Dokumentace XML začíná / / /</span><span class="sxs-lookup"><span data-stu-id="a2e9a-160">XML documentation starts with ///.</span></span> <span data-ttu-id="a2e9a-161">Když vytvoříte nový projekt, uveďte průvodců některé starter / / / řádků v za vás.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-161">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="a2e9a-162">Zpracování tyto komentáře má určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="a2e9a-162">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="a2e9a-163">V dokumentaci musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-163">The documentation must be well-formed XML.</span></span> <span data-ttu-id="a2e9a-164">Pokud není ve správném formátu XML, se generuje upozornění a dokumentaci soubor bude obsahovat komentář, který uvádí, že došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-164">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="a2e9a-165">Vývojáři mohou vytvořit vlastní sadu značky.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-165">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="a2e9a-166">Existuje sada doporučené značky (naleznete v části Další čtení).</span><span class="sxs-lookup"><span data-stu-id="a2e9a-166">There is a recommended set of tags (see the Further Reading section).</span></span> <span data-ttu-id="a2e9a-167">Některé z doporučené značky mají zvláštní význam:</span><span class="sxs-lookup"><span data-stu-id="a2e9a-167">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="a2e9a-168">\<Param > Značka se používá k popisu parametry.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-168">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="a2e9a-169">Pokud se používá, kompilátor ověří, zda parametr existuje a že všechny parametry jsou popsané v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-169">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="a2e9a-170">Pokud ověření selže, vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-170">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="a2e9a-171">`cref` Atributu může být připojen k žádné značky, které poskytují odkaz na element kódu.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-171">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="a2e9a-172">Kompilátor bude ověřte, zda tento element kódu existuje.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-172">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="a2e9a-173">Pokud ověření selže, vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-173">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="a2e9a-174">Kompilátor respektuje žádné `using` příkazy při vypadá pro typ popsané v `cref` atribut.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-174">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="a2e9a-175">\<Souhrnné > Značka se používá technologii IntelliSense v sadě Visual Studio a zobrazte další informace o typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-175">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a2e9a-176">Soubor XML neposkytuje úplné informace o typu a členy (například neobsahuje žádné informace o typu).</span><span class="sxs-lookup"><span data-stu-id="a2e9a-176">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="a2e9a-177">Chcete-li získat úplné informace o typ nebo člen, musí být souborů dokumentace použít současně s reflexe na skutečný typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="a2e9a-177">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e9a-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2e9a-178">See Also</span></span>  
 [<span data-ttu-id="a2e9a-179">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a2e9a-179">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a2e9a-180">/ DOC (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a2e9a-180">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="a2e9a-181">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="a2e9a-181">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
