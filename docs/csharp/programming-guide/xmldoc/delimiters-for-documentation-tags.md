---
title: Oddělovače pro značky dokumentace – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: dd4ddb3b324bd6d235efb541c90875dbe9ed4c2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789821"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Oddělovače pro značky dokumentace (průvodce programováním jazyka C#)

Použití xml doc komentáře vyžaduje oddělovače, které označují kompilátoru, kde komentář dokumentace začíná a končí. S tagy dokumentace XML můžete použít následující typy oddělovačů:

- `///`

  Jednořádkový oddělovač. Toto je formulář, který je zobrazen v příkladech dokumentace a používá visual c# šablony projektu. Pokud je za oddělovačem mezera, není tento znak zahrnut do výstupu XML.

  > [!NOTE]
  > IDE sady Visual Studio má funkci nazvanou Inteligentní \<úpravy \<komentářů, která automaticky vloží značky souhrnných `///`> a /summary> a přesune kurzor v rámci těchto značek po zadání oddělovače v Editoru kódu. Tuto funkci můžete zapnout nebo vypnout v [dialogovém okně Možnosti](/visualstudio/ide/reference/options-text-editor-csharp-advanced).
  
- `/** */`

  Vícesměrové oddělovače.

  Při použití `/** */` oddělovačů je třeba dodržovat určitá pravidla formátování:
  
  - Na řádku, který `/**` obsahuje oddělovač, pokud je zbytek řádku prázdné místo, řádek není zpracován pro komentáře. Pokud je první `/**` znak po oddělovači prázdné místo, tento znak prázdného místa je ignorován a zbytek řádku je zpracován. V opačném případě je celý `/**` text řádku po oddělovači zpracován jako součást komentáře.

  - Na řádku, který `*/` obsahuje oddělovač, pokud je pouze `*/` prázdné místo až k oddělovači, tento řádek je ignorován. V opačném případě je text `*/` na řádku až k oddělovači zpracován jako součást komentáře, s výhradou pravidel pro porovnávání vzorů popsaných v následující odrážce.
  
  - Pro řádky za ten, který `/**` začíná oddělovač, kompilátor hledá společný vzor na začátku každého řádku. Vzorek se může skládat z volitelného`*`prázdného místa a hvězdičky ( ), následované volitelným prázdném místem. Pokud kompilátor najde společný vzor na začátku každého řádku, který nezačíná `/**` oddělovač nebo `*/` oddělovač, ignoruje tento vzor pro každý řádek.

  Následující příklady ilustrují tato pravidla.

  - Jediná část následující poznámky, která bude zpracována, je `<summary>`řádek, který začíná na . Tři formáty značek vytvářejí stejné komentáře.

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - Kompilátor identifikuje společný vzor \* " " na začátku druhého a třetího řádků. Vzor není součástí výstupu.

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - Kompilátor nenajde žádný společný vzor v následující komentář, protože druhý znak na třetím řádku není hvězdičkou. Proto je veškerý text na druhém a třetím řádku zpracován jako součást komentáře.

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - Kompilátor nenajde žádný vzor v následující komentář ze dvou důvodů. Za prvé, počet mezer před hvězdičkou není konzistentní. Za druhé, pátý řádek začíná tabulátorem, který neodpovídá mezerám. Proto je veškerý text z řádků dva až pět zpracován jako součást komentáře.

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

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Komentáře dokumentace XML](./index.md)
- [-doc (možnosti kompilátoru Jazyka C#)](../../language-reference/compiler-options/doc-compiler-option.md)
