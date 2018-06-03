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
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728729"
---
# <a name="how-to-use-the-xml-documentation-features"></a>Postupy: použití funkcí dokumentace XML

Následující příklad obsahuje základní přehled typu, který byly dokumentovány.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

V příkladu generuje soubor .xml s tímto obsahem:

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

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Kompilace v příkladu, zadejte následující příkaz:

`csc XMLsample.cs /doc:XMLsample.xml`

Tento příkaz vytvoří soubor XML *XMLsample.xml*, které lze zobrazit v prohlížeči nebo pomocí příkazu typu.

## <a name="robust-programming"></a>Robustní programování

Dokumentace XML začíná / / / Když vytvoříte nový projekt, uveďte průvodců některé starter / / / řádků v za vás. Zpracování tyto komentáře má určitá omezení:

- V dokumentaci musí být ve správném formátu XML. Pokud není ve správném formátu XML, se generuje upozornění a dokumentaci soubor bude obsahovat komentář, který uvádí, že došlo k chybě.

- Vývojáři mohou vytvořit vlastní sadu značky. Je doporučené sadu značky (viz [doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments.md)). Některé z doporučené značky mají zvláštní význam:

  - \<Param > Značka se používá k popisu parametry. Pokud se používá, kompilátor ověřuje, zda parametr existuje a že všechny parametry jsou popsané v dokumentaci. Pokud ověření selže, vydá upozornění.

  - `cref` Atributu může být připojen k žádné značky, které poskytují odkaz na element kódu. Kompilátor ověří, zda tento element kódu existuje. Pokud ověření selže, vydá upozornění. Kompilátor respektuje žádné `using` příkazy při vypadá pro typ popsané v `cref` atribut.

  - \<Souhrnné > Značka se používá technologii IntelliSense v sadě Visual Studio a zobrazte další informace o typ nebo člen.

    > [!NOTE]
    > Soubor XML neposkytuje úplné informace o typu a členy (například neobsahuje žádné informace o typu). Chcete-li získat úplné informace o typ nebo člen, musí být souborů dokumentace použít současně s reflexe na skutečný typ nebo člen.

## <a name="see-also"></a>Viz také:

[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[/ DOC (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
[Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
