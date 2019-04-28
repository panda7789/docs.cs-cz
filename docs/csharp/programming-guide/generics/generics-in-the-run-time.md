---
title: Obecné typy v běhovém - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: d45d64d608c117ef5f1477ac55a39c192374d7ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680334"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Obecné typy v běhovém prostředí (Průvodce programováním v C#)
Při obecném typu nebo metodě je zkompilován jazyk Microsoft intermediate language (MSIL), obsahuje metadata, která identifikuje tak, že má parametry typu. Jak jazyk MSIL pro obecný typ se používá se liší podle toho, jestli zadaný typ parametru hodnota typu nebo typu odkazu.  
  
 Když obecný typ nejprve zkonstruován s typem hodnoty jako parametr, modul runtime vytvoří specializované obecného typu pomocí zadaného parametrem nebo parametry nahrazeny na příslušných místech v jazyk MSIL. Specializované obecné typy jsou vytvořeny vždy jednou pro každou jedinečnou hodnotu typu, který se používá jako parametr.  
  
 Předpokládejme například, váš kód programu deklarované zásobníku, který je vytvořen celých čísel:  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 V tomto okamžiku modul runtime generuje specializované verze <xref:System.Collections.Generic.Stack%601> třídu, která má nahrazeny odpovídajícím způsobem pro její parametr celé číslo. Teď se pokaždé, když váš program kód používá zásobník celých čísel, generované runtime opětné specializované <xref:System.Collections.Generic.Stack%601> třídy. V následujícím příkladu se vytvoří dvě instance zásobníku celých čísel a sdílejí jednu instanci `Stack<int>` kódu:  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Však Předpokládejme, že to jiné <xref:System.Collections.Generic.Stack%601> třídy pomocí jiného typu hodnoty jako `long` nebo strukturu uživatelem definované jako svůj parametr je vytvořen na jiném místě v kódu. V důsledku toho modul runtime generuje jinou verzi obecného typu a nahradí `long` na příslušných místech v jazyce MSIL. Převody nějaké už nejsou potřebné, protože každý specializované obecnou třídu nativně obsahuje typ hodnoty.  
  
 Obecné typy fungují trochu jinak pro typy odkazů. Při prvním obecného typu je vytvořený pomocí jakéhokoliv odkazového typu, modul runtime vytvoří specializované obecného typu s odkazy na objekty, které jsou nahrazeny pro parametry v jazyk MSIL. Potom pokaždé, když dojde k vytvoření konstruovaný typ s typem odkazu jako svůj parametr, bez ohledu na to, jaký typ je, modul runtime znovu použije dříve vytvořeného specializované verze obecného typu. To je možné, protože jsou všechny odkazy stejnou velikost.  
  
 Předpokládejme například, že jste měli dva typy odkazů `Customer` třídy a `Order` třídy a také Předpokládejme, že jste vytvořili zásobníku `Customer` typy:  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 V tomto okamžiku modul runtime generuje specializované verze <xref:System.Collections.Generic.Stack%601> třída, která obsahuje odkazy na objekty, které se vyplní později místo ukládání dat. Předpokládejme, že další řádek kódu vytvoří zásobníku jiného typu odkaz, který se nazývá `Order`:  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 Na rozdíl od s typy hodnot, jiné specializované verze <xref:System.Collections.Generic.Stack%601> třída není vytvořena pro `Order` typu. Místo toho instance specializované verze <xref:System.Collections.Generic.Stack%601> je vytvořená třída a `orders` proměnná je nastavená na něj odkazovat. Předpokládejme, že pak zjistil psát kód k vytvoření zásobníku `Customer` typu:  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 Stejně jako u předchozí použití <xref:System.Collections.Generic.Stack%601> třídy vytvořené pomocí `Order` zadejte jinou instancí specializované <xref:System.Collections.Generic.Stack%601> je vytvořená třída. Ukazatele, které jsou obsaženy v něm jsou nastavené tak, aby odkazovaly velikost oblasti paměti `Customer` typu. Vzhledem k tomu, že počet typů odkazu se může lišit programu nečekaně implementace jazyka C# obecných typů výrazně snižuje množství kódu do jednoho snížením počtu specializované třídy vytvořený kompilátorem pro obecné třídy odkazových typů.  
  
 Kromě toho při vytvoření instance generické třídy jazyka C# s použitím parametru hodnoty typu nebo odkaz na typ, odraz můžete dotazovat v době běhu a lze zjistit její skutečné typ i jeho typu parametru.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [Obecné typy](~/docs/standard/generics/index.md)
