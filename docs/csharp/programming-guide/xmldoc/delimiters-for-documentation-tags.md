---
title: Oddělovače pro dokumentační značky – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 88ad2519382c06aec2c8b1488c380fac47d5f1a2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588147"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Oddělovače pro dokumentační značky (Průvodce programováním v C#)
Použití komentářů dokumentu XML vyžaduje oddělovače, které označují kompilátoru, kde komentář k dokumentaci začíná a končí. Pomocí značek dokumentace XML můžete použít následující typy oddělovačů:  
  
 `///`  
 Jeden řádek oddělovače. Jedná se o formulář, který je zobrazen v příkladech dokumentace a který se C# používá v šablonách Visual Project. Pokud je za oddělovačem mezera, tento znak není zahrnutý ve výstupu XML.  
  
> [!NOTE]
>  Integrované vývojové prostředí (IDE) sady Visual Studio obsahuje funkci s názvem úpravy inteligentních komentářů, \<která automaticky vkládá \<souhrn > a/Summary > značky a přesune kurzor do těchto `///` značek po zadání oddělovače v editoru kódu. . Tuto funkci můžete zapnout nebo vypnout v [dialogovém okně Možnosti](/visualstudio/ide/reference/options-text-editor-csharp-advanced).  
  
 `/** */`  
 Víceřádkové oddělovače.  
  
 Existují určitá pravidla formátování, která se použijí při použití `/** */` oddělovačů.  
  
- Na řádku, který obsahuje `/**` oddělovač, pokud je zbývající část řádku prázdným znakem, není řádek pro komentáře zpracován. Je-li první znak za `/**` oddělovačem prázdné znaky, bude prázdný znak ignorován a zbytek řádku je zpracován. V opačném případě bude celý text řádku po `/**` oddělovači zpracován jako součást komentáře.  
  
- Na řádku, který obsahuje `*/` oddělovač, pokud je pouze mezera `*/` do oddělovače, tento řádek je ignorován. V opačném případě je text na řádku až do `*/` oddělovače zpracován jako součást komentáře, a to v souladu s pravidly pro porovnávání vzorů popsanými v následující odrážce.  
  
- Pro řádky po jednom, který začíná `/**` oddělovačem, kompilátor hledá společný vzor na začátku každého řádku. Vzor se může skládat z volitelného prázdného místa a hvězdičky (`*`) následovaný více volitelnými prázdnými znaky. Pokud kompilátor najde společný vzor na začátku každého řádku, který nezačíná `/**` oddělovačem `*/` nebo oddělovačem, ignoruje tento model pro každý řádek.  
  
 Tato pravidla ilustrují následující příklady.  
  
- Jediná část následujícího komentáře, který bude zpracována, je řádek, který začíná `<summary>`. Tři formáty značek vytváří stejné komentáře.  
  
    ```csharp  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
- Kompilátor identifikuje běžný vzor "*" na začátku druhého a třetího řádku. Vzorek není zahrnut ve výstupu.  
  
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
  
    ```csharp  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Dokumentační komentáře XML](./index.md)
- [/doc (C# možnosti kompilátoru)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Dokumentační komentáře XML](./index.md)
