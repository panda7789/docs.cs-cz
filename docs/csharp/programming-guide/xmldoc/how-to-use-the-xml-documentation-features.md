---
title: Jak používat funkce dokumentace XML – Průvodce programováním v C#
description: Naučte se používat funkce dokumentace XML. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 9ad2cfe62c70174eec9020ad4c8ce11608aca36d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380667"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="eafbf-104">Jak používat funkce dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="eafbf-104">How to use the XML documentation features</span></span>

<span data-ttu-id="eafbf-105">Následující příklad obsahuje základní přehled o typu, který je dokumentován.</span><span class="sxs-lookup"><span data-stu-id="eafbf-105">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="eafbf-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="eafbf-106">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="eafbf-107">Příklad vygeneruje soubor *. XML* s následujícím obsahem.</span><span class="sxs-lookup"><span data-stu-id="eafbf-107">The example generates an *.xml* file with the following contents.</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="eafbf-108">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="eafbf-108">Compiling the code</span></span>

<span data-ttu-id="eafbf-109">Chcete-li zkompilovat příklad, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="eafbf-109">To compile the example, enter the following command:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="eafbf-110">Tento příkaz vytvoří soubor XML *XMLsample.xml*, který můžete zobrazit v prohlížeči nebo pomocí `TYPE` příkazu.</span><span class="sxs-lookup"><span data-stu-id="eafbf-110">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the `TYPE` command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="eafbf-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="eafbf-111">Robust programming</span></span>

<span data-ttu-id="eafbf-112">Dokumentace XML začíná na `///` .</span><span class="sxs-lookup"><span data-stu-id="eafbf-112">XML documentation starts with `///`.</span></span> <span data-ttu-id="eafbf-113">Když vytvoříte nový projekt, Průvodce vloží `///` do za vás některé úvodní řádky.</span><span class="sxs-lookup"><span data-stu-id="eafbf-113">When you create a new project, the wizards put some starter `///` lines in for you.</span></span> <span data-ttu-id="eafbf-114">Zpracování těchto komentářů má určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="eafbf-114">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="eafbf-115">Dokumentace musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="eafbf-115">The documentation must be well-formed XML.</span></span> <span data-ttu-id="eafbf-116">Pokud XML není ve správném formátu, je vygenerováno upozornění a soubor dokumentace bude obsahovat komentář, který říká, že došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="eafbf-116">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="eafbf-117">Vývojářům je zdarma vytvořit vlastní sadu značek.</span><span class="sxs-lookup"><span data-stu-id="eafbf-117">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="eafbf-118">Je [doporučena sada značek](recommended-tags-for-documentation-comments.md).</span><span class="sxs-lookup"><span data-stu-id="eafbf-118">There is a [recommended set of tags](recommended-tags-for-documentation-comments.md).</span></span> <span data-ttu-id="eafbf-119">Některé z doporučených značek mají zvláštní význam:</span><span class="sxs-lookup"><span data-stu-id="eafbf-119">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="eafbf-120">Tato `<param>` značka se používá k popisu parametrů.</span><span class="sxs-lookup"><span data-stu-id="eafbf-120">The `<param>` tag is used to describe parameters.</span></span> <span data-ttu-id="eafbf-121">Pokud je tento parametr použit, kompilátor ověří, zda existuje parametr a zda jsou všechny parametry popsány v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="eafbf-121">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="eafbf-122">Pokud se ověření nepovede, kompilátor vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="eafbf-122">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="eafbf-123">`cref`Atribut lze připojit k libovolné značce pro odkazování na prvek kódu.</span><span class="sxs-lookup"><span data-stu-id="eafbf-123">The `cref` attribute can be attached to any tag to reference a code element.</span></span> <span data-ttu-id="eafbf-124">Kompilátor ověřuje, zda tento prvek kódu existuje.</span><span class="sxs-lookup"><span data-stu-id="eafbf-124">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="eafbf-125">Pokud se ověření nepovede, kompilátor vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="eafbf-125">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="eafbf-126">Kompilátor respektuje jakékoli `using` příkazy, pokud vyhledává typ popsaný v `cref` atributu.</span><span class="sxs-lookup"><span data-stu-id="eafbf-126">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="eafbf-127">`<summary>`Značka je používána technologií IntelliSense v aplikaci Visual Studio k zobrazení dalších informací o typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="eafbf-127">The `<summary>` tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="eafbf-128">Soubor XML neposkytuje úplné informace o typu a členech (například neobsahuje žádné informace o typu).</span><span class="sxs-lookup"><span data-stu-id="eafbf-128">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="eafbf-129">Chcete-li získat úplné informace o typu nebo členu, použijte soubor dokumentace spolu s reflexí pro skutečný typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="eafbf-129">To get full information about a type or member, use the documentation file together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="eafbf-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eafbf-130">See also</span></span>

- [<span data-ttu-id="eafbf-131">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="eafbf-131">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="eafbf-132">-doc (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="eafbf-132">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="eafbf-133">Komentáře dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="eafbf-133">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="eafbf-134">Procesor dokumentace DocFX</span><span class="sxs-lookup"><span data-stu-id="eafbf-134">DocFX documentation processor</span></span>](https://dotnet.github.io/docfx/)
- [<span data-ttu-id="eafbf-135">Procesor dokumentace Sandcastle</span><span class="sxs-lookup"><span data-stu-id="eafbf-135">Sandcastle documentation processor</span></span>](https://github.com/EWSoftware/SHFB)
