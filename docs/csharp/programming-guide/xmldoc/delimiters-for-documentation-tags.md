---
title: Oddělovače pro dokumentační značky (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 06bd997e6862bc1f86ad2e3b2afbbb5afac78d9c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44064287"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Oddělovače pro dokumentační značky (Průvodce programováním v C#)
Použití komentáře XML vyžaduje oddělovače, které označují kompilátoru kde Dokumentační komentář začíná a končí. Můžete použít následující typy oddělovače se značkami dokumentace XML:  
  
 `///`  
 Oddělovač jedním řádkem. Toto je formulář, který je uvedeno v dokumentaci příklady a používá šablony projektů Visual C#. Pokud je znak mezery za oddělovačem, tento znak není součástí výstupu XML.  
  
> [!NOTE]
>  Integrované vývojové prostředí sady Visual Studio obsahuje funkci s názvem inteligentní úpravy komentářů, který automaticky vloží \<summary > a \</summary > značky a přesune kurzor v rámci těchto značek po zadání `///` oddělovač v editoru kódu . Tuto funkci můžete zapnout nebo vypnout [dialogové okno Možnosti](/visualstudio/ide/reference/options-text-editor-csharp-advanced).  
  
 `/** */`  
 Víceřádkový oddělovače.  
  
 Existují některá pravidla formátování při použití `/** */` oddělovače.  
  
-   Na řádku, který obsahuje `/**` oddělovač, pokud zbytek řádku je prázdný znak řádku není zpracovávána pro poznámky. Pokud po prvním znakem `/**` oddělovač je prázdný znak, že znak bílého prostoru řádku je ignorován a zbytek řádku je zpracovat. V opačném případě celý text řádku po `/**` oddělovač zpracovávány jako součást komentář.  
  
-   Na řádku, který obsahuje `*/` oddělovač, pokud existuje jenom prázdné znaky až `*/` oddělovač, tento řádek se ignoruje. V opačném případě text na řádku až `*/` oddělovač zpracovávány jako součást komentář porovnávání vzorů podle pravidel popsaných v následující odrážky.  
  
-   Pro řádky za ten, který začíná `/**` oddělovač, hledá kompilátor běžný vzor na začátku každého řádku. Vzor se může skládat z volitelné prázdné místo a hvězdičku (`*`) a po něm další volitelné prázdné znaky. Pokud kompilátor najde běžný vzor na začátku každého řádku, který nezačíná `/**` oddělovač nebo `*/` oddělovač, ignoruje tento vzor pro každý řádek.  
  
 Následující příklady znázorňují tato pravidla.  
  
-   Řádek, který začíná je jediná součást následující komentář, který se zpracuje `<summary>`. Tři značky formáty vytvářejí stejné komentáře.  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   Kompilátor identifikuje běžné vzor "*" na začátku druhé a třetí řádky. Vzor není zahrnut ve výstupu.  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   Kompilátor vyhledá žádné běžný vzor v následující komentář, protože druhý znak na třetím řádku není hvězdičku. Proto veškerý text na řádcích druhé a třetí zpracovávány jako součást komentář.  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   Kompilátor vyhledá žádný model v následující komentář dvou důvodů. Počet mezer před hvězdička nejprve není konzistentní. Za druhé pátý řádek začíná kartu, která se neshoduje s mezery. Proto veškerý text z řádky dvou až pět zpracovávány jako součást komentář.  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
- [/ DOC (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
