---
title: 'Postupy: používání funkcí dokumentace XML (C# Programming Guide)'
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 48654968e5099164874bae8a00767d12c8fe4582
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361914"
---
# <a name="how-to-use-the-xml-documentation-features"></a>Postupy: používání funkcí dokumentace XML

Následující příklad obsahuje základní přehled o typ, který má zdokumentované.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

Tento příklad generuje soubor .xml s následujícím obsahem:

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

## <a name="compiling-the-code"></a>Kompilování kódu

Chcete-li příklad zkompilovat, zadejte na příkazovém řádku následující:

`csc XMLsample.cs /doc:XMLsample.xml`

Tento příkaz vytvoří soubor XML *XMLsample.xml*, který můžete zobrazit v prohlížeči nebo pomocí příkazu typu.

## <a name="robust-programming"></a>Robustní programování

Dokumentace XML začíná / / / / /. Když vytvoříte nový projekt, umístěte průvodců starter / / / / / řádků v za vás. Zpracování tyto poznámky platí některá omezení:

- V dokumentaci k musí být ve správném formátu XML. Pokud kód XML není ve správném formátu, je vygenerováno upozornění a dokumentaci soubor bude obsahovat komentář, který říká, že došlo k chybě.

- Vývojáři jsou zdarma vytvořit vlastní sadu značek. Je doporučené sady značek (viz [doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments.md)). Některé doporučené značky mají zvláštní význam:

  - \<Param > Značka se používá k popisu parametrů. Pokud použijete, kompilátor ověří, že parametr existuje a že všechny parametry jsou popsané v dokumentaci. Pokud ověření se nezdařilo, kompilátor vyvolá upozornění.

  - `cref` Atribut lze připojit ke každé značce poskytnout odkaz na prvek kódu. Kompilátor ověří, zda tento prvek kódu existuje. Pokud ověření se nezdařilo, kompilátor vyvolá upozornění. Kompilátor respektuje žádné `using` příkazy při typu je popsáno v `cref` atribut.

  - \<Summary > Značka se používá technologie IntelliSense v sadě Visual Studio zobrazíte další informace o typu nebo členu.

    > [!NOTE]
    > Soubor XML neposkytuje úplné informace o typu a členů (například neobsahuje žádné informace o typu). Pokud chcete získat úplné informace o typu nebo členu, musí použít soubor dokumentace společně reflexe na skutečný typ nebo člen.

## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [/ DOC (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
