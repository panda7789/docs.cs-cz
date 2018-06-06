---
title: 'Postupy: použití funkcí dokumentace XML (C# Průvodce programováním)'
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: b82f92cc034a13e8867cfb56866200101ab77b9b
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728729"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="d7467-102">Postupy: použití funkcí dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="d7467-102">How to: Use the XML documentation features</span></span>

<span data-ttu-id="d7467-103">Následující příklad obsahuje základní přehled typu, který byly dokumentovány.</span><span class="sxs-lookup"><span data-stu-id="d7467-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="d7467-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7467-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="d7467-105">V příkladu generuje soubor .xml s tímto obsahem:</span><span class="sxs-lookup"><span data-stu-id="d7467-105">The example generates an .xml file with the following contents:</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xmlsample</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            <summary>
            Class level summary documentation goes here.
            </summary>
            <remarks>
            Longer comments can be associated with a type or member through
            the remarks tag.
            </remarks>
        </member>
        <member name="F:TestClass._name">
            <summary>
            Store for the Name property.
            </summary>
        </member>
        <member name="M:TestClass.#ctor">
            <summary>
            The class constructor.
            </summary>
        </member>
        <member name="P:TestClass.Name">
            <summary>
            Name property.
            </summary>
            <value>
            A value tag is used to describe the property value.
            </value>
        </member>
        <member name="M:TestClass.SomeMethod(System.String)">
            <summary>
            Description for SomeMethod.
            </summary>
            <param name="s"> Parameter description for s goes here.</param>
            <seealso cref="T:System.String">
            You can use the cref attribute on any tag to reference a type or member 
            and the compiler will check that the reference exists.
            </seealso>
        </member>
        <member name="M:TestClass.SomeOtherMethod">
            <summary>
            Some other method.
            </summary>
            <returns>
            Return values are described through the returns tag.
            </returns>
            <seealso cref="M:TestClass.SomeMethod(System.String)">
            Notice the use of the cref attribute to reference a specific method.
            </seealso>
        </member>
        <member name="M:TestClass.Main(System.String[])">
            <summary>
            The entry point for the application.
            </summary>
            <param name="args"> A list of command line arguments.</param>
        </member>
        <member name="T:TestInterface">
            <summary>
            Documentation that describes the interface goes here.
            </summary>
            <remarks>
            Details about the interface go here.
            </remarks>
        </member>
        <member name="M:TestInterface.InterfaceMethod(System.Int32)">
            <summary>
            Documentation that describes the method goes here.
            </summary>
            <param name="n">
            Parameter n requires an integer argument.
            </param>
            <returns>
            The method returns an integer.
            </returns>
        </member>
    </members>
</doc>
```

## <a name="compiling-the-code"></a><span data-ttu-id="d7467-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d7467-106">Compiling the code</span></span>

<span data-ttu-id="d7467-107">Kompilace v příkladu, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d7467-107">To compile the example, type the following command line:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="d7467-108">Tento příkaz vytvoří soubor XML *XMLsample.xml*, které lze zobrazit v prohlížeči nebo pomocí příkazu typu.</span><span class="sxs-lookup"><span data-stu-id="d7467-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the TYPE command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="d7467-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d7467-109">Robust programming</span></span>

<span data-ttu-id="d7467-110">Dokumentace XML začíná / / /</span><span class="sxs-lookup"><span data-stu-id="d7467-110">XML documentation starts with ///.</span></span> <span data-ttu-id="d7467-111">Když vytvoříte nový projekt, uveďte průvodců některé starter / / / řádků v za vás.</span><span class="sxs-lookup"><span data-stu-id="d7467-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="d7467-112">Zpracování tyto komentáře má určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="d7467-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="d7467-113">V dokumentaci musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="d7467-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="d7467-114">Pokud není ve správném formátu XML, se generuje upozornění a dokumentaci soubor bude obsahovat komentář, který uvádí, že došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="d7467-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="d7467-115">Vývojáři mohou vytvořit vlastní sadu značky.</span><span class="sxs-lookup"><span data-stu-id="d7467-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="d7467-116">Je doporučené sadu značky (viz [doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="d7467-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="d7467-117">Některé z doporučené značky mají zvláštní význam:</span><span class="sxs-lookup"><span data-stu-id="d7467-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="d7467-118">\<Param > Značka se používá k popisu parametry.</span><span class="sxs-lookup"><span data-stu-id="d7467-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="d7467-119">Pokud se používá, kompilátor ověřuje, zda parametr existuje a že všechny parametry jsou popsané v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="d7467-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="d7467-120">Pokud ověření selže, vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="d7467-120">If the verification failed, the compiler issues a warning.</span></span>

  - <span data-ttu-id="d7467-121">`cref` Atributu může být připojen k žádné značky, které poskytují odkaz na element kódu.</span><span class="sxs-lookup"><span data-stu-id="d7467-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="d7467-122">Kompilátor ověří, zda tento element kódu existuje.</span><span class="sxs-lookup"><span data-stu-id="d7467-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="d7467-123">Pokud ověření selže, vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="d7467-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="d7467-124">Kompilátor respektuje žádné `using` příkazy při vypadá pro typ popsané v `cref` atribut.</span><span class="sxs-lookup"><span data-stu-id="d7467-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="d7467-125">\<Souhrnné > Značka se používá technologii IntelliSense v sadě Visual Studio a zobrazte další informace o typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="d7467-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d7467-126">Soubor XML neposkytuje úplné informace o typu a členy (například neobsahuje žádné informace o typu).</span><span class="sxs-lookup"><span data-stu-id="d7467-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="d7467-127">Chcete-li získat úplné informace o typ nebo člen, musí být souborů dokumentace použít současně s reflexe na skutečný typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="d7467-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7467-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7467-128">See also</span></span>

[<span data-ttu-id="d7467-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d7467-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="d7467-130">/ DOC (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="d7467-130">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
[<span data-ttu-id="d7467-131">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="d7467-131">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
