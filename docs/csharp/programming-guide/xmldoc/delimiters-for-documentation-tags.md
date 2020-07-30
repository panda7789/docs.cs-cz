---
title: Oddělovače pro dokumentační značky – Průvodce programováním v C#
description: Seznamte se s oddělovači pro dokumentaci k dokumentaci. Oddělovače označují kompilátoru, kde komentář k dokumentaci začíná a končí.
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 3191e32b0ff2dbde004abaab0b699cd61fcbb150
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381980"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Oddělovače pro dokumentační značky (Průvodce programováním v C#)

Použití komentářů dokumentu XML vyžaduje oddělovače, které označují kompilátoru, kde komentář k dokumentaci začíná a končí. Pomocí značek dokumentace XML můžete použít následující typy oddělovačů:

- `///`

  Jeden řádek oddělovače. Jedná se o formulář, který je zobrazen v příkladech dokumentace a používá šablony projektů v jazyce C#. Pokud je za oddělovačem mezera, tento znak není zahrnutý ve výstupu XML.

  > [!NOTE]
  > Integrované vývojové prostředí (IDE) sady Visual Studio `<summary>` `</summary>` po zadání `///` oddělovače v editoru kódu automaticky vloží značky a a přesune kurzor do těchto značek. Tuto funkci můžete zapnout nebo vypnout v [dialogovém okně Možnosti](/visualstudio/ide/reference/options-text-editor-csharp-advanced).
  
- `/** */`

  Víceřádkové oddělovače.

  Existují určitá pravidla formátování, která se použijí při použití `/** */` oddělovačů:
  
  - Na řádku, který obsahuje `/**` oddělovač, pokud je zbývající část řádku prázdným znakem, není řádek pro komentáře zpracován. Je-li první znak za `/**` oddělovačem prázdné znaky, bude prázdný znak ignorován a zbytek řádku je zpracován. V opačném případě bude celý text řádku po `/**` oddělovači zpracován jako součást komentáře.

  - Na řádku, který obsahuje `*/` oddělovač, pokud je pouze mezera do `*/` oddělovače, tento řádek je ignorován. V opačném případě se text na řádku do `*/` oddělovače zpracuje jako součást komentáře.
  
  - Pro řádky po jednom, který začíná `/**` oddělovačem, kompilátor hledá společný vzor na začátku každého řádku. Vzor se může skládat z volitelného prázdného místa a hvězdičky ( `*` ) následovaný více volitelnými prázdnými znaky. Pokud kompilátor najde společný vzor na začátku každého řádku, který nezačíná `/**` oddělovačem nebo oddělovačem `*/` , ignoruje tento model pro každý řádek.

  Tato pravidla ilustrují následující příklady.

  - Jediná část následujícího komentáře, který je zpracována, je řádek, který začíná `<summary>` . Tři formáty značek vytváří stejné komentáře.

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - Kompilátor identifikuje společný vzor " \* " na začátku druhého a třetího řádku. Vzorek není zahrnut ve výstupu.

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - Kompilátor nenajde žádný společný vzor v následujícím komentáři, protože druhý znak na třetím řádku není hvězdička. Proto je veškerý text na druhém a třetím řádku zpracován jako součást komentáře.

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - Kompilátor nenajde z následujících komentářů žádný vzor, ze dvou důvodů. Za prvé je počet mezer před hvězdičkou nekonzistentní. Za druhé, pátá čára začíná tabulátorem, který se neshoduje s mezerami. Proto se veškerý text z řádků dvou až pěti zpracovává jako součást komentáře.

    <!-- markdownlint-disable MD010 -->
    ```csharp
    /**
      * <summary>
      * text
     *  text2
        *  </summary>
    */
    ```
    <!-- markdownlint-enable MD010 -->

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Komentáře dokumentace XML](./index.md)
- [-doc (možnosti kompilátoru C#)](../../language-reference/compiler-options/doc-compiler-option.md)
