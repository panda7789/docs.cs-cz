---
title: Použití funkcí dokumentace XML – C# Průvodce programováním
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 5de94b1f1ab44f954b5bab9f8b5212c33325c19d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696711"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="fa592-102">Jak používat funkce dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="fa592-102">How to use the XML documentation features</span></span>

<span data-ttu-id="fa592-103">Následující příklad obsahuje základní přehled o typu, který je dokumentován.</span><span class="sxs-lookup"><span data-stu-id="fa592-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="fa592-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa592-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="fa592-105">Příklad vygeneruje soubor. XML s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="fa592-105">The example generates an .xml file with the following contents:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="fa592-106">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="fa592-106">Compiling the code</span></span>

<span data-ttu-id="fa592-107">Chcete-li zkompilovat příklad, zadejte následující příkazový řádek:</span><span class="sxs-lookup"><span data-stu-id="fa592-107">To compile the example, type the following command line:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="fa592-108">Tento příkaz vytvoří soubor XML *XMLsample. XML*, který lze zobrazit v prohlížeči nebo pomocí příkazu Type.</span><span class="sxs-lookup"><span data-stu-id="fa592-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the TYPE command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="fa592-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="fa592-109">Robust programming</span></span>

<span data-ttu-id="fa592-110">Dokumentace XML začíná na///.</span><span class="sxs-lookup"><span data-stu-id="fa592-110">XML documentation starts with ///.</span></span> <span data-ttu-id="fa592-111">Při vytváření nového projektu Průvodce vloží do za vás některé počáteční///řádky.</span><span class="sxs-lookup"><span data-stu-id="fa592-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="fa592-112">Zpracování těchto komentářů má určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="fa592-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="fa592-113">Dokumentace musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="fa592-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="fa592-114">Pokud XML není ve správném formátu, je vygenerováno upozornění a soubor dokumentace bude obsahovat komentář, který říká, že došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="fa592-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="fa592-115">Vývojářům je zdarma vytvořit vlastní sadu značek.</span><span class="sxs-lookup"><span data-stu-id="fa592-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="fa592-116">Je doporučena sada značek (viz téma [Doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="fa592-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="fa592-117">Některé z doporučených značek mají zvláštní význam:</span><span class="sxs-lookup"><span data-stu-id="fa592-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="fa592-118">K popisu parametrů se používá značka \<param >.</span><span class="sxs-lookup"><span data-stu-id="fa592-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="fa592-119">Pokud je tento parametr použit, kompilátor ověří, zda existuje parametr a zda jsou všechny parametry popsány v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="fa592-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="fa592-120">Pokud se ověření nepovedlo, kompilátor vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="fa592-120">If the verification failed, the compiler issues a warning.</span></span>

  - <span data-ttu-id="fa592-121">Atribut `cref` lze připojit k libovolné značce k poskytnutí odkazu na prvek kódu.</span><span class="sxs-lookup"><span data-stu-id="fa592-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="fa592-122">Kompilátor ověřuje, zda tento prvek kódu existuje.</span><span class="sxs-lookup"><span data-stu-id="fa592-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="fa592-123">Pokud se ověření nepovedlo, kompilátor vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="fa592-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="fa592-124">Kompilátor respektuje jakékoli `using` příkazy, pokud hledá typ popsaný v atributu `cref`.</span><span class="sxs-lookup"><span data-stu-id="fa592-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="fa592-125">Inteligentní > Značka \<je používána technologií IntelliSense v aplikaci Visual Studio k zobrazení dalších informací o typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="fa592-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fa592-126">Soubor XML neposkytuje úplné informace o typu a členech (například neobsahuje žádné informace o typu).</span><span class="sxs-lookup"><span data-stu-id="fa592-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="fa592-127">Chcete-li získat úplné informace o typu nebo členu, je nutné použít soubor dokumentace spolu s reflexí pro skutečný typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="fa592-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa592-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa592-128">See also</span></span>

- [<span data-ttu-id="fa592-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fa592-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fa592-130">-doc (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="fa592-130">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="fa592-131">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="fa592-131">XML Documentation Comments</span></span>](./index.md)
- [<span data-ttu-id="fa592-132">Procesor dokumentace DocFX</span><span class="sxs-lookup"><span data-stu-id="fa592-132">DocFX documentation processor</span></span>](https://dotnet.github.io/docfx/)
- [<span data-ttu-id="fa592-133">Procesor dokumentace Sandcastle</span><span class="sxs-lookup"><span data-stu-id="fa592-133">Sandcastle documentation processor</span></span>](https://github.com/EWSoftware/SHFB)
