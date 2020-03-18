---
title: Použití funkcí dokumentace XML – průvodce programováním jazyka C#
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: e279b13d9216120e25f454faa14dc71ad24c74ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156997"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="6ce86-102">Jak používat funkce dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="6ce86-102">How to use the XML documentation features</span></span>

<span data-ttu-id="6ce86-103">Následující ukázka obsahuje základní přehled typu, který byl zdokumentován.</span><span class="sxs-lookup"><span data-stu-id="6ce86-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="6ce86-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ce86-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="6ce86-105">Příklad generuje soubor *XML* s následujícím obsahem.</span><span class="sxs-lookup"><span data-stu-id="6ce86-105">The example generates an *.xml* file with the following contents.</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="6ce86-106">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="6ce86-106">Compiling the code</span></span>

<span data-ttu-id="6ce86-107">Chcete-li zkompilovat příklad, zadejte následující příkazový řádek:</span><span class="sxs-lookup"><span data-stu-id="6ce86-107">To compile the example, type the following command line:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="6ce86-108">Tento příkaz vytvoří soubor XML *XMLsample.xml*, který můžete zobrazit v prohlížeči nebo pomocí příkazu TYP.</span><span class="sxs-lookup"><span data-stu-id="6ce86-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the TYPE command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="6ce86-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6ce86-109">Robust programming</span></span>

<span data-ttu-id="6ce86-110">Dokumentace XML začíná na ///.</span><span class="sxs-lookup"><span data-stu-id="6ce86-110">XML documentation starts with ///.</span></span> <span data-ttu-id="6ce86-111">Když vytvoříte nový projekt, průvodci zasadí některé řádky startéru /// pro vás.</span><span class="sxs-lookup"><span data-stu-id="6ce86-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="6ce86-112">Zpracování těchto připomínek má určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="6ce86-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="6ce86-113">Dokumentace musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="6ce86-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="6ce86-114">Pokud xml není ve správném formátu, je generováno upozornění a soubor dokumentace bude obsahovat komentář, který říká, že došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="6ce86-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="6ce86-115">Vývojáři mohou vytvořit vlastní sadu značek.</span><span class="sxs-lookup"><span data-stu-id="6ce86-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="6ce86-116">K dispozici je [doporučená sada značek](recommended-tags-for-documentation-comments.md).</span><span class="sxs-lookup"><span data-stu-id="6ce86-116">There is a [recommended set of tags](recommended-tags-for-documentation-comments.md).</span></span> <span data-ttu-id="6ce86-117">Některé z doporučených značek mají zvláštní význam:</span><span class="sxs-lookup"><span data-stu-id="6ce86-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="6ce86-118">Značka \<param> se používá k popisu parametrů.</span><span class="sxs-lookup"><span data-stu-id="6ce86-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="6ce86-119">Pokud je použit, kompilátor ověří, zda parametr existuje a že všechny parametry jsou popsány v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="6ce86-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="6ce86-120">Pokud se ověření nezdařilo, kompilátor vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="6ce86-120">If the verification failed, the compiler issues a warning.</span></span>

  - <span data-ttu-id="6ce86-121">Atribut `cref` lze připojit k libovolné značce poskytnout odkaz na prvek kódu.</span><span class="sxs-lookup"><span data-stu-id="6ce86-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="6ce86-122">Kompilátor ověří, zda tento prvek kódu existuje.</span><span class="sxs-lookup"><span data-stu-id="6ce86-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="6ce86-123">Pokud se ověření nezdařilo, kompilátor vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="6ce86-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="6ce86-124">Kompilátor respektuje `using` všechny příkazy, když hledá typ `cref` popsaný v atributu.</span><span class="sxs-lookup"><span data-stu-id="6ce86-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="6ce86-125">Značka \<souhrnné> používá technologie IntelliSense v sadě Visual Studio k zobrazení dalších informací o typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="6ce86-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6ce86-126">Soubor XML neposkytuje úplné informace o typu a členy (například neobsahuje žádné informace o typu).</span><span class="sxs-lookup"><span data-stu-id="6ce86-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="6ce86-127">Chcete-li získat úplné informace o typu nebo členu, musí být soubor dokumentace použit společně s reflexí skutečného typu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="6ce86-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ce86-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ce86-128">See also</span></span>

- [<span data-ttu-id="6ce86-129">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6ce86-129">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6ce86-130">-doc (možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6ce86-130">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="6ce86-131">Komentáře dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="6ce86-131">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="6ce86-132">Dokumentační procesor DocFX</span><span class="sxs-lookup"><span data-stu-id="6ce86-132">DocFX documentation processor</span></span>](https://dotnet.github.io/docfx/)
- [<span data-ttu-id="6ce86-133">Dokumentační procesor Sandcastle</span><span class="sxs-lookup"><span data-stu-id="6ce86-133">Sandcastle documentation processor</span></span>](https://github.com/EWSoftware/SHFB)
