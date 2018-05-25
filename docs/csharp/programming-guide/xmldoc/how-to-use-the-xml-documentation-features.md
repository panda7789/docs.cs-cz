---
title: 'Postupy: Použití funkcí dokumentace XML (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: d7f1f51040033cf25f7f1aefb04d249e6e028ca3
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2018
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="432d0-102">Postupy: Použití funkcí dokumentace XML (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="432d0-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="432d0-103">Následující příklad obsahuje základní přehled typu, který byly dokumentovány.</span><span class="sxs-lookup"><span data-stu-id="432d0-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="432d0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="432d0-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  

<span data-ttu-id="432d0-105">V příkladu generuje soubor .xml s tímto obsahem:</span><span class="sxs-lookup"><span data-stu-id="432d0-105">The example generates an .xml file with the following contents:</span></span>

```xml  
<?xml version="1.0"?>  
<doc>  
 <assembly>  
 <name>xmlsample</name>  
 </assembly>  
 <members>  
 <member name="T:SomeClass">  
 <summary>  
 Class level summary documentation goes here.</summary>  
 <remarks>  
 Longer comments can be associated with a type or member  
 through the remarks tag</remarks>  
 </member>  
 <member name="F:SomeClass.m_Name">  
 <summary>  
 Store for the name property</summary>  
 </member>  
 <member name="M:SomeClass.#ctor">  
 <summary>The class constructor.</summary>  
 </member>  
 <member name="M:SomeClass.SomeMethod(System.String)">  
 <summary>  
 Description for SomeMethod.</summary>  
 <param name="s"> Parameter description for s goes here</param>  
 <seealso cref="T:System.String">  
 You can use the cref attribute on any tag to reference a type or member  
 and the compiler will check that the reference exists. </seealso>  
 </member>  
 <member name="M:SomeClass.SomeOtherMethod">  
 <summary>  
 Some other method. </summary>  
 <returns>  
 Return results are described through the returns tag.</returns>  
 <seealso cref="M:SomeClass.SomeMethod(System.String)">  
 Notice the use of the cref attribute to reference a specific method </seealso>  
 </member>  
 <member name="M:SomeClass.Main(System.String[])">  
 <summary>  
 The entry point for the application.  
 </summary>  
 <param name="args"> A list of command line arguments</param>  
 </member>  
 <member name="P:SomeClass.Name">  
 <summary>  
 Name property </summary>  
 <value>A value tag is used to describe the property value</value>  
 </member>  
 </members>  
</doc>   
```

## <a name="compiling-the-code"></a><span data-ttu-id="432d0-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="432d0-106">Compiling the Code</span></span>  
 <span data-ttu-id="432d0-107">Kompilace v příkladu, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="432d0-107">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="432d0-108">Tím se vytvoří soubor XML XMLsample.xml, které lze zobrazit v prohlížeči nebo pomocí příkazu typu.</span><span class="sxs-lookup"><span data-stu-id="432d0-108">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="432d0-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="432d0-109">Robust Programming</span></span>  
 <span data-ttu-id="432d0-110">Dokumentace XML začíná / / /</span><span class="sxs-lookup"><span data-stu-id="432d0-110">XML documentation starts with ///.</span></span> <span data-ttu-id="432d0-111">Když vytvoříte nový projekt, uveďte průvodců některé starter / / / řádků v za vás.</span><span class="sxs-lookup"><span data-stu-id="432d0-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="432d0-112">Zpracování tyto komentáře má určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="432d0-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="432d0-113">V dokumentaci musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="432d0-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="432d0-114">Pokud není ve správném formátu XML, se generuje upozornění a dokumentaci soubor bude obsahovat komentář, který uvádí, že došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="432d0-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="432d0-115">Vývojáři mohou vytvořit vlastní sadu značky.</span><span class="sxs-lookup"><span data-stu-id="432d0-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="432d0-116">Je doporučené sadu značky (viz [doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="432d0-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="432d0-117">Některé z doporučené značky mají zvláštní význam:</span><span class="sxs-lookup"><span data-stu-id="432d0-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="432d0-118">\<Param > Značka se používá k popisu parametry.</span><span class="sxs-lookup"><span data-stu-id="432d0-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="432d0-119">Pokud se používá, kompilátor ověří, zda parametr existuje a že všechny parametry jsou popsané v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="432d0-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="432d0-120">Pokud ověření selže, vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="432d0-120">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="432d0-121">`cref` Atributu může být připojen k žádné značky, které poskytují odkaz na element kódu.</span><span class="sxs-lookup"><span data-stu-id="432d0-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="432d0-122">Kompilátor bude ověřte, zda tento element kódu existuje.</span><span class="sxs-lookup"><span data-stu-id="432d0-122">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="432d0-123">Pokud ověření selže, vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="432d0-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="432d0-124">Kompilátor respektuje žádné `using` příkazy při vypadá pro typ popsané v `cref` atribut.</span><span class="sxs-lookup"><span data-stu-id="432d0-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="432d0-125">\<Souhrnné > Značka se používá technologii IntelliSense v sadě Visual Studio a zobrazte další informace o typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="432d0-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="432d0-126">Soubor XML neposkytuje úplné informace o typu a členy (například neobsahuje žádné informace o typu).</span><span class="sxs-lookup"><span data-stu-id="432d0-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="432d0-127">Chcete-li získat úplné informace o typ nebo člen, musí být souborů dokumentace použít současně s reflexe na skutečný typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="432d0-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="432d0-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="432d0-128">See Also</span></span>  
 [<span data-ttu-id="432d0-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="432d0-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="432d0-130">/ DOC (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="432d0-130">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="432d0-131">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="432d0-131">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
