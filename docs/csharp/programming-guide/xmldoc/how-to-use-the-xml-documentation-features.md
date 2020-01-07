---
title: Použití funkcí dokumentace XML – C# Průvodce programováním
ms.custom: seodec18
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 40b90bd12687becacddf2e75c39057683b43b945
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634986"
---
# <a name="how-to-use-the-xml-documentation-features"></a>Jak používat funkce dokumentace XML

Následující příklad obsahuje základní přehled o typu, který je dokumentován.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

Příklad vygeneruje soubor. XML s následujícím obsahem:

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

Tento příkaz vytvoří soubor XML *XMLsample. XML*, který lze zobrazit v prohlížeči nebo pomocí příkazu Type.

## <a name="robust-programming"></a>Robustní programování

Dokumentace XML začíná na///. Při vytváření nového projektu Průvodce vloží do za vás některé počáteční///řádky. Zpracování těchto komentářů má určitá omezení:

- Dokumentace musí být ve správném formátu XML. Pokud XML není ve správném formátu, je vygenerováno upozornění a soubor dokumentace bude obsahovat komentář, který říká, že došlo k chybě.

- Vývojářům je zdarma vytvořit vlastní sadu značek. Je doporučena sada značek (viz téma [Doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments.md)). Některé z doporučených značek mají zvláštní význam:

  - K popisu parametrů se používá značka \<param >. Pokud je tento parametr použit, kompilátor ověří, zda existuje parametr a zda jsou všechny parametry popsány v dokumentaci. Pokud se ověření nepovedlo, kompilátor vydá upozornění.

  - Atribut `cref` lze připojit k libovolné značce k poskytnutí odkazu na prvek kódu. Kompilátor ověřuje, zda tento prvek kódu existuje. Pokud se ověření nepovedlo, kompilátor vydá upozornění. Kompilátor respektuje jakékoli `using` příkazy, pokud hledá typ popsaný v atributu `cref`.

  - Inteligentní > Značka \<je používána technologií IntelliSense v aplikaci Visual Studio k zobrazení dalších informací o typu nebo členu.

    > [!NOTE]
    > Soubor XML neposkytuje úplné informace o typu a členech (například neobsahuje žádné informace o typu). Chcete-li získat úplné informace o typu nebo členu, je nutné použít soubor dokumentace spolu s reflexí pro skutečný typ nebo člen.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [-doc (C# možnosti kompilátoru)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Dokumentační komentáře XML](./index.md)
- [Procesor dokumentace DocFX](https://dotnet.github.io/docfx/)
- [Procesor dokumentace Sandcastle](https://github.com/EWSoftware/SHFB)
