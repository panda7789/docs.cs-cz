---
title: "Oddělovače pro dokumentační značky (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a6ab03d220d1ef71605b83c529595dd986ea922a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Oddělovače pro dokumentační značky (Průvodce programováním v C#)
Použití komentáře doc XML vyžaduje oddělovače, které označují kompilátoru kde komentáře dokumentace k zahájení a ukončení. Můžete použít následující typy oddělovače s dokumentační značky XML:  
  
 `///`  
 Oddělovač jeden řádek. Toto je formulář, který je zobrazeno v příkladech dokumentace a použít šablony projektů Visual C#. Pokud je prázdný znak za oddělovačem, tento znak není zahrnut ve výstupu XML.  
  
> [!NOTE]
>  Visual Studio IDE má funkci inteligentního komentář úpravy, které automaticky vloží \<souhrnné > a \<nebo souhrnných > značky a přesune kurzor v rámci těchto značek po zadání `///` oddělovač v editoru kódu . Přístup k této funkci z [možnosti, textový Editor, C#, formátování vzorků](/visualstudio/ide/reference/options-text-editor-csharp-formatting) na stránkách vlastností projektu.  
  
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [/ DOC (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
