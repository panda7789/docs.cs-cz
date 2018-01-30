---
title: "Oddělovače pro dokumentační značky (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0c72ee03ff8a2e28bec1ba83e42cd7f201b140ed
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Oddělovače pro dokumentační značky (Průvodce programováním v C#)
Použití komentáře doc XML vyžaduje oddělovače, které označují kompilátoru kde komentáře dokumentace k zahájení a ukončení. Můžete použít následující typy oddělovače s dokumentační značky XML:  
  
 `///`  
 Oddělovač jeden řádek. Toto je formulář, který je zobrazeno v příkladech dokumentace a použít šablony projektů Visual C#. Pokud je prázdný znak za oddělovačem, tento znak není zahrnut ve výstupu XML.  
  
> [!NOTE]
>  Visual Studio IDE má funkci inteligentního komentář úpravy, které automaticky vloží \<souhrnné > a \<nebo souhrnných > značky a přesune kurzor v rámci těchto značek po zadání `///` oddělovač v editoru kódu . Tuto funkci můžete zapnout nebo vypnout [dialogové okno Možnosti](/visualstudio/ide/reference/options-text-editor-csharp-advanced).  
  
 `/** */`  
 Víceřádkový oddělovače.  
  
 Existují některé formátování pravidla při použití `/** */` oddělovače.  
  
-   Na řádku, který obsahuje `/**` oddělovač, pokud zbývající řádku je prázdné znaky, řádek není zpracován pro komentáře. Pokud po první znak `/**` oddělovač je prázdný znak, že prázdný znak je ignorován a zbytek řádku je zpracovat. V opačném celý text řádku po `/**` oddělovač zpracovávány jako součást komentář.  
  
-   Na řádek, který obsahuje `*/` oddělovač, pokud je pouze mezera až `*/` oddělovač, daného řádku je ignorováno. Jinak hodnota textu v řádku než `*/` oddělovač zpracovávány jako součást komentář, dodržování pravidel porovnávání popsané v následující odrážka.  
  
-   Řádků po ten, který začíná `/**` oddělovač, kompilátor hledá společný vzorek na začátku každého řádku. Vzor se může skládat z mezer volitelné a znak hvězdičky (`*`), za nímž následují další volitelné mezer. Pokud kompilátor vyhledá společný vzorek na začátku každého řádku, který začíná `/**` oddělovač nebo `*/` oddělovač, ignoruje tento vzor pro každý řádek.  
  
 Následující příklady znázorňují tato pravidla.  
  
-   Část pouze následující komentář, který bude zpracován je řádek, který začíná `<summary>`. Formáty tři označení vytvořit stejné komentáře.  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   Kompilátor identifikuje běžný vzor "*" na začátku druhé a třetí řádky. Vzor není zahrnut ve výstupu.  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   Kompilátor žádný společný vzorek najde v následující komentář protože znacích na ve třetím řádku není hvězdičku. Proto je veškerý text na řádcích druhé a třetí zpracovat jako součást komentář.  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   Kompilátor vyhledá žádné vzor v následující komentář dvou důvodů. Počet mezer, než se tedy hvězdička nejprve není konzistentní. Druhý páté řádek začíná na kartě, který neodpovídá prostory. Proto je veškerý text z čar dva až pět zpracovat jako součást komentář.  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [/doc (C# Compiler Options)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
