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
# <a name="how-to-use-the-xml-documentation-features"></a>Jak používat funkce dokumentace XML

Následující ukázka obsahuje základní přehled typu, který byl zdokumentován.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

Příklad generuje soubor *XML* s následujícím obsahem.

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

## <a name="compiling-the-code"></a>Zkompilování kódu

Chcete-li zkompilovat příklad, zadejte následující příkazový řádek:

`csc XMLsample.cs /doc:XMLsample.xml`

Tento příkaz vytvoří soubor XML *XMLsample.xml*, který můžete zobrazit v prohlížeči nebo pomocí příkazu TYP.

## <a name="robust-programming"></a>Robustní programování

Dokumentace XML začíná na ///. Když vytvoříte nový projekt, průvodci zasadí některé řádky startéru /// pro vás. Zpracování těchto připomínek má určitá omezení:

- Dokumentace musí být ve správném formátu XML. Pokud xml není ve správném formátu, je generováno upozornění a soubor dokumentace bude obsahovat komentář, který říká, že došlo k chybě.

- Vývojáři mohou vytvořit vlastní sadu značek. K dispozici je [doporučená sada značek](recommended-tags-for-documentation-comments.md). Některé z doporučených značek mají zvláštní význam:

  - Značka \<param> se používá k popisu parametrů. Pokud je použit, kompilátor ověří, zda parametr existuje a že všechny parametry jsou popsány v dokumentaci. Pokud se ověření nezdařilo, kompilátor vydá upozornění.

  - Atribut `cref` lze připojit k libovolné značce poskytnout odkaz na prvek kódu. Kompilátor ověří, zda tento prvek kódu existuje. Pokud se ověření nezdařilo, kompilátor vydá upozornění. Kompilátor respektuje `using` všechny příkazy, když hledá typ `cref` popsaný v atributu.

  - Značka \<souhrnné> používá technologie IntelliSense v sadě Visual Studio k zobrazení dalších informací o typu nebo členu.

    > [!NOTE]
    > Soubor XML neposkytuje úplné informace o typu a členy (například neobsahuje žádné informace o typu). Chcete-li získat úplné informace o typu nebo členu, musí být soubor dokumentace použit společně s reflexí skutečného typu nebo člena.

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [-doc (možnosti kompilátoru Jazyka C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentáře dokumentace XML](./index.md)
- [Dokumentační procesor DocFX](https://dotnet.github.io/docfx/)
- [Dokumentační procesor Sandcastle](https://github.com/EWSoftware/SHFB)
