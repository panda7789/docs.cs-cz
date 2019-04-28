---
title: 'Postupy: Použití funkcí dokumentace XML - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 893dc726f7b4ee2d2afa69f63d13d1f11a4692db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708194"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="24842-102">Postupy: Použití funkcí dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="24842-102">How to: Use the XML documentation features</span></span>

<span data-ttu-id="24842-103">Následující příklad obsahuje základní přehled o typ, který má zdokumentované.</span><span class="sxs-lookup"><span data-stu-id="24842-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="24842-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="24842-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="24842-105">Tento příklad generuje soubor .xml s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="24842-105">The example generates an .xml file with the following contents:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="24842-106">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="24842-106">Compiling the code</span></span>

<span data-ttu-id="24842-107">Chcete-li příklad zkompilovat, zadejte na příkazovém řádku následující:</span><span class="sxs-lookup"><span data-stu-id="24842-107">To compile the example, type the following command line:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="24842-108">Tento příkaz vytvoří soubor XML *XMLsample.xml*, který můžete zobrazit v prohlížeči nebo pomocí příkazu typu.</span><span class="sxs-lookup"><span data-stu-id="24842-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the TYPE command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="24842-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="24842-109">Robust programming</span></span>

<span data-ttu-id="24842-110">Dokumentace XML začíná / / / / /.</span><span class="sxs-lookup"><span data-stu-id="24842-110">XML documentation starts with ///.</span></span> <span data-ttu-id="24842-111">Když vytvoříte nový projekt, umístěte průvodců starter / / / / / řádků v za vás.</span><span class="sxs-lookup"><span data-stu-id="24842-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="24842-112">Zpracování tyto poznámky platí některá omezení:</span><span class="sxs-lookup"><span data-stu-id="24842-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="24842-113">V dokumentaci k musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="24842-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="24842-114">Pokud kód XML není ve správném formátu, je vygenerováno upozornění a dokumentaci soubor bude obsahovat komentář, který říká, že došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="24842-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="24842-115">Vývojáři jsou zdarma vytvořit vlastní sadu značek.</span><span class="sxs-lookup"><span data-stu-id="24842-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="24842-116">Je doporučené sady značek (viz [doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="24842-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="24842-117">Některé doporučené značky mají zvláštní význam:</span><span class="sxs-lookup"><span data-stu-id="24842-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="24842-118">\<Param > Značka se používá k popisu parametrů.</span><span class="sxs-lookup"><span data-stu-id="24842-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="24842-119">Pokud použijete, kompilátor ověří, že parametr existuje a že všechny parametry jsou popsané v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="24842-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="24842-120">Pokud ověření se nezdařilo, kompilátor vyvolá upozornění.</span><span class="sxs-lookup"><span data-stu-id="24842-120">If the verification failed, the compiler issues a warning.</span></span>

  - <span data-ttu-id="24842-121">`cref` Atribut lze připojit ke každé značce poskytnout odkaz na prvek kódu.</span><span class="sxs-lookup"><span data-stu-id="24842-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="24842-122">Kompilátor ověří, zda tento prvek kódu existuje.</span><span class="sxs-lookup"><span data-stu-id="24842-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="24842-123">Pokud ověření se nezdařilo, kompilátor vyvolá upozornění.</span><span class="sxs-lookup"><span data-stu-id="24842-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="24842-124">Kompilátor respektuje žádné `using` příkazy při typu je popsáno v `cref` atribut.</span><span class="sxs-lookup"><span data-stu-id="24842-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="24842-125">\<Summary > Značka se používá technologie IntelliSense v sadě Visual Studio zobrazíte další informace o typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="24842-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="24842-126">Soubor XML neposkytuje úplné informace o typu a členů (například neobsahuje žádné informace o typu).</span><span class="sxs-lookup"><span data-stu-id="24842-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="24842-127">Pokud chcete získat úplné informace o typu nebo členu, musí použít soubor dokumentace společně reflexe na skutečný typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="24842-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="24842-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24842-128">See also</span></span>

- [<span data-ttu-id="24842-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="24842-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="24842-130">/ DOC (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="24842-130">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="24842-131">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="24842-131">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
