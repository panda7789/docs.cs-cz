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
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a>Postupy: Použití funkcí dokumentace XML (Průvodce programováním v C#)
Následující příklad obsahuje základní přehled typu, který byly dokumentovány.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  

V příkladu generuje soubor .xml s tímto obsahem:

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

## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace v příkladu, zadejte následující příkaz:  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 Tím se vytvoří soubor XML XMLsample.xml, které lze zobrazit v prohlížeči nebo pomocí příkazu typu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Dokumentace XML začíná / / / Když vytvoříte nový projekt, uveďte průvodců některé starter / / / řádků v za vás. Zpracování tyto komentáře má určitá omezení:  
  
-   V dokumentaci musí být ve správném formátu XML. Pokud není ve správném formátu XML, se generuje upozornění a dokumentaci soubor bude obsahovat komentář, který uvádí, že došlo k chybě.  
  
-   Vývojáři mohou vytvořit vlastní sadu značky. Je doporučené sadu značky (viz [doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments.md)). Některé z doporučené značky mají zvláštní význam:  
  
    -   \<Param > Značka se používá k popisu parametry. Pokud se používá, kompilátor ověří, zda parametr existuje a že všechny parametry jsou popsané v dokumentaci. Pokud ověření selže, vydá upozornění.  
  
    -   `cref` Atributu může být připojen k žádné značky, které poskytují odkaz na element kódu. Kompilátor bude ověřte, zda tento element kódu existuje. Pokud ověření selže, vydá upozornění. Kompilátor respektuje žádné `using` příkazy při vypadá pro typ popsané v `cref` atribut.  
  
    -   \<Souhrnné > Značka se používá technologii IntelliSense v sadě Visual Studio a zobrazte další informace o typ nebo člen.  
  
        > [!NOTE]
        >  Soubor XML neposkytuje úplné informace o typu a členy (například neobsahuje žádné informace o typu). Chcete-li získat úplné informace o typ nebo člen, musí být souborů dokumentace použít současně s reflexe na skutečný typ nebo člen.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [/ DOC (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
